# Finance Control Panel Restriction GPO

## Objective

Create and validate a Group Policy Object that prevents Finance users from accessing Control Panel and Windows Settings without affecting users in other departments.

## Scope

The GPO was linked to:

`home.lab → Accounts → Finance`

The `Alexis.finance` user account resides inside the Finance OU.

## Configuration

A GPO named `Finance-Restricted Control Panel` was created and linked directly to the Finance OU.

Configured setting:

`User Configuration → Policies → Administrative Templates → Control Panel → Prohibit access to Control Panel and PC settings`

The setting was configured as **Enabled**.

## Group Policy Inheritance

The Finance OU receives:

- `Finance-Restricted Control Panel`, linked directly to Finance
- `Drive Mapping`, inherited from the parent Accounts OU

This demonstrates that child OUs process applicable policies inherited from their parent OUs in addition to policies linked directly to them.

## Policy Deployment

On PC01, I signed in using the `Alexis.finance` domain account and refreshed Group Policy:

```cmd
gpupdate /force
