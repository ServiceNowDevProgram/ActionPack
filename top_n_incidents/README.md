Top N Incidents for Assignment Group 

This flow action fetch the Top N incidents assigned to a specific Assignment group for summaries, and notifications.

---

## What it does
Returns a JSON array of incident records for a given **sys_user_group** by sorting options (Resent, Updated, Priority) as per specified limit.

---

## Inputs
- **group** *(String, required)* — `sys_user_group.sys_id` of the target group  
- **limit** *(Integer, default: 5)* — how many incidents to return  
- **sort** *(Choice, default: `priority`)* — `priority | recent | updated`  
  - `priority` → lowest priority number first (1 → 5), then newest `opened_at`  
  - `recent` → newest `opened_at` first  
  - `updated` → newest `sys_updated_on` first  
- **open_only** *(Boolean, default: true)* — `true` to include only active incidents

---

## Outputs
- **incidents_json** *(String)* — JSON array of incident rows  
- **count** *(Integer)* — number of incidents returned

**Each incident row includes:**
```json
{
  "sys_id": "...",
  "number": "INC0012345",
  "short_description": "Something broke",
  "priority": 2,
  "priority_display": "2 - High",
  "state": 2,
  "state_display": "In Progress",
  "opened_at": "2025-10-01 12:34:56",
  "sys_updated_on": "2025-10-05 09:20:00",
  "caller_id": "6816f79cc0a8016401c5a33be04be441",
  "caller_display": "Abel Tuter",
  "assignment_group": "287ebd7da9fe198100f92cc8d1d2154e",
  "assignment_group_display": "Network"
}
