## Dataverse Tables

### Employees
- EmployeeID (Auto Number)
- Name (Text)
- Email (Text)
- Department (Choice: HR, Finance, IT, Sales, Ops)
- StartDate (DateOnly)
- Status (Choice: Pending Approval, Approved, Rejected)
- ManagerEmail (Text)
- CreatedOn (Auto)

### Approvals
- ApprovalID (Auto Number)
- Employee (Lookup → Employees)
- ApproverEmail (Text)
- Decision (Choice: Pending, Approved, Rejected)
- DecisionOn (DateTime)
- Comments (Multiline)

### Tasks
- TaskID (Auto Number)
- Employee (Lookup → Employees)
- TaskName (Text)
- Owner (Text)
- DueDate (DateOnly)
- Status (Choice: Not Started, In Progress, Done)
