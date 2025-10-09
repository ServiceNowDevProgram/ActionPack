README — Get Current On-Call Users (Flow Action)
Purpose:
This Flow Designer Custom Action retrieves the current on-call user(s) for a specified assignment group in ServiceNow using the On-Call Scheduling API.
It can be used in Flows or Subflows to automatically assign incidents, notify escalation contacts, or integrate with messaging systems (Slack, Twilio, etc.).

<img width="1917" height="944" alt="image" src="https://github.com/user-attachments/assets/bbe7fe6a-7418-4c28-9f77-d03dbf64417f" />


🧭 Overview

When triggered, this action:

Looks up the current date/time or a specified timestamp.

Calls global.OnCallRotation().whoIsOnCall() to determine who’s on-call.

Returns a JSON list of all active on-call members (Primary, Secondary, etc.).

Exposes the first on-call member separately for easy assignment or alerting.

⚙️ Inputs
Name	Type	Required	Description
group_sys_id	String	✅ Yes	The sys_id of the target sys_user_group (e.g., “Major Incident Managers”).
when	Date/Time	No	Optional — specific time to check coverage. Defaults to current time.
📤 Outputs
Name	Type	Description
users_json	String	JSON array of on-call user details (sys_id, name, email, phone).
count	Integer	Total number of users found in the on-call list.
first_user_sys_id	String	Sys ID of the primary on-call user.
first_user_name	String	Name of the primary on-call user.
first_user_email	String	Email address of the primary on-call user.
first_user_phone	String	Phone number of the primary on-call user.
🧠 Script Logic (Core)
(function execute(inputs, outputs) {
    if (!inputs.group_sys_id) {
        throw new Error('group_sys_id is required');
    }

    var rota = new global.OnCallRotation();
    var gdt = inputs.when ? new GlideDateTime(inputs.when) : new GlideDateTime();
    var list = rota.whoIsOnCall(inputs.group_sys_id + '', '', '', gdt);

    var users = [];
    if (list && list.length && list.length > 0) {
        for (var i = 0; i < list.length; i++) {
            var member = list[i];
            var userSysId = member.userSysId || member.userId;

            if (userSysId) {
                var userGR = new GlideRecord('sys_user');
                if (userGR.get(userSysId)) {
                    users.push({
                        order: i,
                        sys_id: userGR.getUniqueValue(),
                        name: userGR.getDisplayValue(),
                        email: (userGR.email || '').toString(),
                        phone: (userGR.mobile_phone || userGR.phone || '').toString()
                    });
                }
            }
        }
    }

    outputs.users_json = JSON.stringify(users);
    outputs.count = users.length;

    outputs.first_user_sys_id  = users[0] ? users[0].sys_id  : '';
    outputs.first_user_name    = users[0] ? users[0].name    : '';
    outputs.first_user_email   = users[0] ? users[0].email   : '';
    outputs.first_user_phone   = users[0] ? users[0].phone   : '';

})(inputs, outputs);

🧩 Usage Example

Flow: “Auto-Assign Major Incident to On-Call Manager”

Trigger: Major Incident Created

Action: Get Current On-Call Users

group_sys_id = e3abf0a8db20b2000ea6fb37bf961969

Condition: count > 0

Set field: Assigned to = ${first_user_sys_id}

Send notification: “Paging ${first_user_name} (on call)”

Else: Fallback to queue or send escalation email.

🧱 Dependencies

Plugin: On-Call Scheduling (com.snc.on_call_rotation)

Tables Accessed:

sys_user

cmn_rota (via API call)

Roles:

admin or any role with read access to On-Call tables.

🧩 Testing
Scenario	Expected Result
Group has active on-call rotation	Returns 1+ users in users_json
Group has no rotation	Returns count = 0
Future when value	Returns users scheduled at that time
Invalid group_sys_id	Script throws error message
⚠️ Notes & Gotchas

Use global.OnCallRotation(), not SNC.OnCallRotation(), for global scope.

The whoIsOnCall() API returns a JavaScript array, not a GlideRecord list.

The first returned user (index 0) is treated as Primary; subsequent ones are Secondary/Backup.

Ensure on-call rosters are configured with valid coverage windows and active users.

If you want to include future shifts, modify the script to iterate over days with addDaysUTC().
