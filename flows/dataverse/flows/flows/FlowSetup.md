# Flow Setup (Power Automate)

1) Go to https://make.powerautomate.com → Environments: select your target.
2) Create a **Solution** named `EmployeeOnboarding`.
3) Inside the solution → **New → Cloud flow → Automated**.
4) Trigger: **Dataverse → When a row is added → Table: Employees**.
5) Add action: **Office 365 Users → Get manager (V2)** (optional if you already store ManagerEmail).
6) Add action: **Approvals → Start and wait for an approval**.
   - Approval type: Approve/Reject – First to respond
   - Assigned to: `ManagerEmail` (from trigger)
   - Title/details: use dynamic fields (Name, Department, StartDate)
7) Add **Condition**: `Outcome` equals `Approve`.
   - **If Yes**:
     - **Dataverse → Update row** (Employees.Status = Approved)
     - **Teams → Post message** to HR channel
   - **If No**:
     - **Dataverse → Update row** (Employees.Status = Rejected)
     - **Outlook → Send an email (V2)** to `Email` (employee)
8) Save → Test with a new Employees record (Status should change automatically).
