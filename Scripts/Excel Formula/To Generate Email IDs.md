# Generate email IDs automatically using the username, or the username and father's name.



### Scenario 1: Username to Email ID

**Assumption**

- **Column A** = Username
    

**Formula**

```excel
=A2 & "@coolie.com"
```

**Example**

| Username   | Generated Email                                       |
| ---------- | ----------------------------------------------------- |
| powerhouse | [powerhouse@coolie.com](mailto:powerhouse@coolie.com) |
| Rajini     | [Rajini@coolie.com](mailto:john@coolie.com)           |
| Lokesh     | [Lokesh@coolie.com](mailto:alice@coolie.com)          |

---

### Scenario 2: Username + Father's Name to Email ID

**Assumption**

- **Column A** = Username
    
- **Column B** = Father's Name
    

**Formula**

```excel
=LOWER(A2 & "." & B2 & "@coolie.com")
```

**Example**

| Username | Father's Name | Generated Email                                               |
| -------- | ------------- | ------------------------------------------------------------- |
| Shruti   | Kamal         | [Shruti.kamal@coolie.com](mailto:powerhouse.kumar@coolie.com) |
| John     | David         | [john.david@coolie.com](mailto:john.david@coolie.com)         |
| Alice    | Smith         | [alice.smith@coolie.com](mailto:alice.smith@coolie.com)       |

---

## Notes

- Replace `@coolie.com` with your organization's email domain if required.
    
- `LOWER()` converts the entire email address to lowercase.
    
- The `&` operator joins text values together.
    
- Fill the formula down to apply it to all rows in the spreadsheet.