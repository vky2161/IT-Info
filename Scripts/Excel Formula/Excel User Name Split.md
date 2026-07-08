# Excel User Name Split - Quick Reference

## Purpose

In IT Support work, you may receive user lists where the full name is stored in one Excel column.

Example:

![](../../images/Excel_Name_Split.png)


The requirement is to separate:

- First Name → Column A
    
- Father Name / Last Name → Column B
    

Result:

| First Name | Father Name |
| ---------- | ----------- |
| Toruk      | Makto       |
| Paul       | Atreides    |
| Tony       | Stark       |

---

# Method 1: Using Excel Formula (Recommended)

## Step 1: Extract First Name

Assume the full name is in cell **A2**.

In the first name column:

```excel
=TEXTBEFORE(A2," ")
```

Output:
![](../../images/Excel_Name_2.png)

---

## Step 2: Extract Second Name

In the second name column:

```excel
=TEXTAFTER(A2," ")
```

Output:
![](../../images/Excel_name_1.png)


## Step 3: Apply to All Users

For 30 users:

1. Enter the formula in the first row.
    
2. Press Enter.
    
3. Drag the fill handle down.
    
4. Excel will automatically apply the formula to all rows.
    

---

# Method 2: Older Excel Versions

If TEXTBEFORE and TEXTAFTER are not available:

## Extract First Name

```excel
=LEFT(A2,FIND(" ",A2)-1)
```

Example:

Input:

```
Toruk Makto
```

Output:

```
Toruk
```

---

## Extract Second Name

```excel
=RIGHT(A2,LEN(A2)-FIND(" ",A2))
```

Example:

Input:

```
Toruk Makto
```

Output:

```
Makto
```

---

# Method 3: Text to Columns (Fastest Method)

For large user lists:

1. Select the full name column.
    
2. Go to:
    

```
Data → Text to Columns
```

3. Select:
    

```
Delimited
```

4. Choose:
    

```
Space
```

5. Click:
    

```
Finish
```

Excel automatically separates:

Before:

```
Toruk Makto
```

After:

```
Toruk | Makto
```

---

# IT Support Use Cases

This method is useful for:

- Active Directory user creation lists
    
- Employee onboarding sheets
    
- HR user data cleanup
    
- Bulk account creation
    
- Email ID generation
    
- Asset management reports
    

---

# Example: Preparing AD User Data

Original:

| Full Name  |
| ---------- |
| Tony Stark |

After split:

| First Name | Last Name |
| ---------- | --------- |
| Tony       |  Stark    |

Possible AD username:

```
Tony.Stark
```

Possible email:

```
Tony.Stark@company.com
```

---

# Quick Reminder

|Task|Tool|
|---|---|
|Split names quickly|Text to Columns|
|Dynamic split|TEXTBEFORE/TEXTAFTER|
|Older Excel support|LEFT/FIND/RIGHT formulas|
|User account preparation|Excel + PowerShell|

---

## Learning Note

Excel formulas like these are valuable for IT Support because many real-world tasks involve cleaning and preparing user data before importing it into systems like:

- Active Directory
    
- Microsoft 365
    
- Ticketing systems
    
- Asset management tools

***
