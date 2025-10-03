
## Overview
This Flow Action allows you to check if a given user belongs to a specified group in ServiceNow. 

## Inputs
- **User** (Reference → `sys_user`): The user you want to check.  
- **Group** (Reference → `sys_user_group`): The group to check against.

  ## Outputs
- **Is Member** (true/false):  
  - `true` → User is in the group  
  - `false` → User is not in the group
    
We can use this Action in flows to save time by quickly looking up and checking if a particular user is in the group before continuing with the follow-up steps.
