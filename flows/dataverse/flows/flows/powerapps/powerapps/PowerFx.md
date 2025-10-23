# Power Fx Snippets

## Submit Employee (OnSelect of "Submit" button)
Patch(
    Employees,
    Defaults(Employees),
    {
        Name: txtName.Text,
        Email: txtEmail.Text,
        Department: drpDepartment.Selected.Value,
        StartDate: dteStart.SelectedDate,
        Status: "Pending Approval",
        ManagerEmail: txtManagerEmail.Text
    }
);
Notify("Employee submitted for approval.", NotificationType.Success);

## Gallery Items (Employees by newest)
Sort(Employees, CreatedOn, SortOrder.Descending)
