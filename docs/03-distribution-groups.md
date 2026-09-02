Overview

This lab demonstrates several common Active Directory administrative tasks in the `home.lab` domain. The work included creating groups for different purposes, confirming group membership and Group Policy processing, and following an account-management procedure for a disabled user.

## Finance security group

A global security group named `SG-Finance-Users` was created in the `Accounts/Finance` organizational unit (OU). A security group allows permissions and policies to be assigned to a group instead of being configured separately for every Finance user. The global scope is appropriate for collecting user accounts from the same domain.


### Membership and policy verification

The Finance user `Taylor.finance` was associated with `SG-Finance-Users`. Group membership was verified from the user's workstation with `whoami /groups`. The output shows `HOME\SG-Finance-Users` as an enabled group in the user's current security token.


Group Policy processing was also checked with `gpresult`. The results show that the `Finance-Restricted Control Panel` and `Drive Mapping` Group Policy Objects were applied to the user. The output also lists `SG-Finance-Users` among the user's security groups, confirming that the Finance account received the expected group-based configuration.


## IT announcements distribution group

An `IT-Announcements` group was configured for sending announcements to IT personnel. It uses the **Universal** scope and **Distribution** type. Unlike a security group, a distribution group is intended for message distribution rather than assigning access permissions.

The group description states that it contains IT member accounts for announcements.


The membership list was reviewed to confirm the accounts included in the group. The screenshot shows the IT and administrative lab accounts `Ethan`, `Ethan-Admin`, `Helpdesk`, and `sysadmin` as members.


## Disabled-user account procedure

The `Taylor.finance` account was disabled in Active Directory Users and Computers. Disabling the account prevents it from being used to authenticate while preserving the directory object, its attributes, and its existing configuration for auditing or possible recovery.


After it was disabled, the account was moved from the Finance OU to the dedicated `Accounts/Disabled Users` OU. Keeping disabled accounts in a separate OU makes them easier to identify, review, manage, and apply dedicated policies to without immediately deleting them.


## Result

The lab established role-based administration and a basic account-lifecycle process:

- Finance users can be managed through the `SG-Finance-Users` security group.
- Group membership and resulting Group Policy application were verified on a domain workstation.
- IT announcement recipients are organized through a dedicated distribution group.
- A disabled account was retained and isolated in a dedicated OU rather than being deleted.

These practices make access, policy assignment, communication groups, and inactive-account management easier to administer and audit.
