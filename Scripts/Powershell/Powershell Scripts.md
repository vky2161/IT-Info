# PowerShell Active Directory 

## Introduction

PowerShell is a command-line tool used by IT administrators to automate Windows administration tasks.

For Active Directory (AD), PowerShell helps with:

- User management
    
- Group management
    
- Computer management
    
- Password resets
    
- Account troubleshooting
    
- Reporting
    

Before using AD PowerShell commands, install/import the Active Directory module:

```powershell
Import-Module ActiveDirectory
```

---

# 1. Find a User in Active Directory

### Command:

```powershell
Get-ADUser -Identity username
```

### Example:

```powershell
Get-ADUser -Identity john.smith
```

Purpose:

- Check if a user exists in AD.
    
- View basic user information.
    

---

# 2. Display User Details

```powershell
Get-ADUser -Identity john.smith -Properties *
```

Purpose:

- Shows all available user attributes.
    

Useful fields:

- Name
    
- Email
    
- Department
    
- Last login time
    
- Account status
    

---

# 3. Search Users by Name

```powershell
Get-ADUser -Filter "Name -like '*John*'"
```

Purpose:

- Find users when you know only part of their name.
    

---

# 4. Create a New AD User

Example:

```powershell
New-ADUser `
-Name "David Kumar" `
-GivenName "David" `
-Surname "Kumar" `
-SamAccountName "david.kumar" `
-UserPrincipalName "david.kumar@company.com" `
-Enabled $true
```

Purpose:

- Create a new user account.
    

Note:

- In real environments, additional settings are usually required.
    

---

# 5. Disable a User Account

```powershell
Disable-ADAccount -Identity username
```

Example:

```powershell
Disable-ADAccount -Identity david.kumar
```

Purpose:

- Disable accounts for resigned employees or security reasons.
    

---

# 6. Enable a User Account

```powershell
Enable-ADAccount -Identity username
```

Purpose:

- Reactivate a disabled account.
    

---

# 7. Unlock a Locked User Account

```powershell
Unlock-ADAccount -Identity username
```

Purpose:

- Used when users are locked after multiple failed login attempts.
    

---

# 8. Reset User Password

```powershell
Set-ADAccountPassword `
-Identity username `
-Reset `
-NewPassword (ConvertTo-SecureString "NewPassword@123" -AsPlainText -Force)
```

Purpose:

- Reset forgotten passwords.
    

Note:

- Follow company password policies.
    

---

# 9. Check User Account Status

```powershell
Get-ADUser username -Properties Enabled
```

Example Output:

```
Enabled : True
```

Purpose:

- Check if an account is active.
    

---

# 10. Add User to a Group

Example:

```powershell
Add-ADGroupMember `
-Identity "IT Support" `
-Members username
```

Purpose:

- Add users to security groups.
    

---

# 11. Remove User from a Group

```powershell
Remove-ADGroupMember `
-Identity "IT Support" `
-Members username
```

Purpose:

- Remove user permissions.
    

---

# 12. View Group Members

```powershell
Get-ADGroupMember "IT Support"
```

Purpose:

- Check who belongs to a group.
    

---

# 13. Find Computers in Active Directory

```powershell
Get-ADComputer -Filter *
```

Purpose:

- List all computers joined to the domain.
    

---

# 14. Disable a Computer Account

```powershell
Disable-ADAccount -Identity ComputerName
```

Purpose:

- Disable old or unused computer accounts.
    

---

# 15. Export Users to CSV Report

```powershell
Get-ADUser -Filter * |
Select Name,SamAccountName,Enabled |
Export-Csv C:\ADUsers.csv -NoTypeInformation
```

Purpose:

- Create an AD user report.
    

---

# 16. Check Last Login Time

```powershell
Get-ADUser username -Properties LastLogonDate
```

Purpose:

- Check when a user last logged in.
    

---

# 17. Find Disabled Users

```powershell
Search-ADAccount -AccountDisabled
```

Purpose:

- List disabled accounts.
    

---

# 18. Find Locked Users

```powershell
Search-ADAccount -LockedOut
```

Purpose:

- Troubleshoot login problems.
    

---

# Useful AD PowerShell Commands Summary

|Task|Command|
|---|---|
|Find user|Get-ADUser|
|Create user|New-ADUser|
|Disable user|Disable-ADAccount|
|Enable user|Enable-ADAccount|
|Unlock account|Unlock-ADAccount|
|Reset password|Set-ADAccountPassword|
|Manage groups|Add-ADGroupMember|
|View computers|Get-ADComputer|
|Export report|Export-Csv|

---

# Learning Practice Ideas

Create a test environment and practice:

1. Create a test user.
    
2. Add user to a group.
    
3. Disable the account.
    
4. Unlock the account.
    
5. Reset the password.
    
6. Export a user report.
    


---

