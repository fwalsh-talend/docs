---
tap-reference: "deputy"

version: "1.0"

foreign-keys:
  - id: "-id"
    attribute: ""
    table: ""
    all-foreign-keys:
      - table: ""
        join-on: "Id"

  - id: "address-id"
    attribute: "Address"
    table: "addresses"
    all-foreign-keys:
      - table: "addresses"
        join-on: "Id"
      - table: "companies"
      - table: "employee_history"
        join-on: "MailAddress"
      - table: "employee_history"
        join-on: "PostalAddress"
      - table: "employee_history"
        join-on: "EmergencyAddress"
      - table: "operational_units"

  - id: "category-id"
    attribute: "EmploymentCategory"
    table: "categories"
    all-foreign-keys:
      - table: "categories"
        join-on: "Id"
      - table: "employee_contracts"
      - table: "employment_conditions"

  - id: "company-id"
    attribute: "Company"
    table: "companies"
    all-foreign-keys:
      - table: "companies"
        join-on: "Id"
      - table: "companies"
        join-on: "ParentCompany"
      - table: "company_periods"
      - table: "employee_history"
      - table: "employee_workplaces"
      - table: "kiosk"
      - table: "leaves"
      - table: "system_usage_tracking"

  - id: "company-period-id"
    attribute: "Period"
    table: "company_periods"
    all-foreign-keys:
      - table: "company_periods"
        join-on: "Id"
      - table: "employee_paycycles"
        join-on: "PeriodId"

  - id: "contact-id"
    attribute: "Contact"
    table: "contacts"
    all-foreign-keys:
      - table: "contacts"
        join-on: "Id"
      - table: "companies"
      - table: "operational_units"

  - id: "country-id"
    attribute: "Country"
    table: "countries"
    all-foreign-keys:
      - table: "countries"
        join-on: "Id"
      - table: "geo"
      - table: "states"

  - id: "custom-field-data-id"
    attribute: "CustomFieldData"
    table: "custom_field_data"
    all-foreign-keys:
      - table: "custom_field_data"
        join-on: "Id"
      - table: "timesheets"

  - id: "custom-field-id"
    attribute: "CustomField"
    table: "custom_fields"
    all-foreign-keys:
      - table: "custom_fields"
        join-on: "Id"

  - id: "employee-id"
    attribute: "Employee"
    table: "employees"
    all-foreign-keys:
      - table: "employees"
        join-on: "Id"
      - table: "custom_app_data"
      - table: "employee_agreements"
        join-on: "EmployeeId"
      - table: "employee_appraisal"
        join-on: "EmployeeId"
      - table: "employee_availability"
        join-on: "EmployeeId"
      - table: "employee_history"
        join-on: "EmployeeId"
      - table: "employee_paycycles"
        join-on: "EmployeeId"
      - table: "employee_salary_opunit_costing"
      - table: "employee_workplaces"
        join-on: "EmployeeId"
      - table: "geo"
      - table: "journal"
      - table: "kiosk"
      - table: "leave_accruals"
      - table: "leaves"
      - table: "roster_opens"
      - table: "roster_swaps"
      - table: "rosters"
      - table: "rosters"
        join-on: "ConfirmBy"
      - table: "sales_data"
      - table: "teams"
        join-on: "LeaderEmployee"
      - table: "timesheets"
      - table: "training_records"
      - table: "[any_table]"
        join-on: "Creator"

  - id: "employee-agreement-history-id"
    attribute: "EmployeeAgreementHistory"
    table: "employee_agreements_history"
    all-foreign-keys:
      - table: "employee_agreements_history"
        join-on: "Id"
      - table: "employee_agreementss"
        join-on: "HistoryId"
      - table: "employee_paycycles"
        join-on: "EmployeeAgreementHistoryId"
      - table: "employee_salary_opunit_costing"

  - id: "employee-agreement-id"
    attribute: "EmployeeAgreement"
    table: "employee_agreements"
    all-foreign-keys:
      - table: "employee_agreements_history"
      - table: "employee_agreements"
        join-on: "Id"
      - table: "employee_paycycles"
      - table: "employee_salary_opunit_costing"
      - table: "employee_workplaces"
        join-on: "Agreement1"
      - table: "employee_workplaces"
        join-on: "Agreement2"
      - table: "employee_workplaces"
        join-on: "Agreement3"
      - table: "leave_pay_lines"
      - table: "timesheets"

  - id: "employee-availability-id"
    attribute: ""
    table: "employee_availability"
    all-foreign-keys:
      - table: "employee_availability"
        join-on: "Id"

  - id: "employee-contract-id"
    attribute: "Contract"
    table: "employee_contracts"
    all-foreign-keys:
      - table: "employee_agreements_history"
      - table: "employee_agreements"
      - table: "employee_contract_leave_rules"
        join-on: "ContractId"
      - table: "employee_contracts"
        join-on: "Id"

  - id: "employee-contract-leave-id"
    attribute: ""
    table: "employee_contract_leave_rules"
    all-foreign-keys:
      - table: "employee_contract_leave_rules"
        join-on: "Id"

  - id: "employee-history-id"
    attribute: "EmployeeHistory"
    table: "employee_history"
    all-foreign-keys:
      - table: "employee_history"
        join-on: "Id"
      - table: "leaves"
      - table: "timesheets"

  - id: "employee-paycycle-return-id"
    attribute: "PaycycleId"
    table: "employee_paycycle_returns"
    all-foreign-keys:
      - table: "employee_paycycle_returns"
        join-on: "Id"
      - table: "timesheets"

  - id: "employee-paycycle--id"
    attribute: "Paycycle"
    table: "employee_paycycles"
    all-foreign-keys:
      - table: "employee_paycycle_returns"
        join-on: "PaycycleId"
      - table: "employee_paycycles"
        join-on: "Id"

  - id: "employee-role-id"
    attribute: "Role"
    table: "employee_roles"
    all-foreign-keys:
      - table: "employee_history"
      - table: "employee_roles"
        join-on: "Id"

  - id: "employment-condition-id-id"
    attribute: "EmploymentCondition"
    table: "employment_conditions"
    all-foreign-keys:
      - table: "employee_contracts"
      - table: "employment_conditions"
        join-on: "Id"

  - id: "event-id"
    attribute: "Event"
    table: "events"
    all-foreign-keys:
      - table: "events"
        join-on: "Id"

  - id: "journal-id"
    attribute: "Journal"
    table: "journal"
    all-foreign-keys:
      - table: "journal"
        join-on: "Id"

  - id: "kiosk-id"
    attribute: "Kiosk"
    table: "kiosk"
    all-foreign-keys:
      - table: "kiosk"
        join-on: "Id"

  - id: "leave-id"
    attribute: "Leave"
    table: "leaves"
    all-foreign-keys:
      - table: "leave_pay_lines"
        join-on: "LeaveId"
      - table: "leaves"
        join-on: "Id"
      - table: "timesheets"
        join-on: "LeaveId"

  - id: "leave-accrual-id"
    attribute: "LeaveAccrual"
    table: "leave_accruals"
    all-foreign-keys:
      - table: "leave_accruals"
        join-on: "Id"

  - id: "leave-pay-line-id"
    attribute: "LeavePayLine"
    table: "leave_pay_lines"
    all-foreign-keys:
      - table: "leave_pay_lines"
        join-on: "Id"

  - id: "leave-rule-id"
    attribute: "LeaveRule"
    table: "leave_rules"
    all-foreign-keys:
      - table: "employee_contract_leave_rules"
        join-on: "LeaveRuleId"
      - table: "leave_accruals"
      - table: "leave_pay_lines"
      - table: "leave_rules"
        join-on: "Id"
      - table: "timesheets"

  - id: "operational-unit-id"
    attribute: "OpUnit"
    table: "operational_units"
    all-foreign-keys:
      - table: "employee_salary_opunit_costing"
      - table: "operational_units"
        join-on: "Id"
      - table: "operational_units"
        join-on: "ParentOperationalUnit"
      - table: "rosters"
        join-on: "OperationalUnit"
      - table: "sales_data"
      - table: "task_groups"
        join-on: "OpUnitId"
      - table: "task_opunit_configs"
        join-on: "OpUnitId"
      - table: "tasks"
        join-on: "OpUnitId"
      - table: "timesheets"
        join-on: "OperationalUnit"

  - id: "pay-period-id"
    attribute: "PayPeriod"
    table: "pay_periods"
    all-foreign-keys:
      - table: "pay_periods"
        join-on: "Id"
      - table: "company_periods"
      - table: "employee_agreements_history"
      - table: "employee_agreements"

  - id: "pay-rule-id"
    attribute: "PayRule"
    table: "pay_rules"
    all-foreign-keys:
      - table: "employee_agreements_history"
        join-on: "SalaryPayRule"
      - table: "employee_agreements"
        join-on: "SalaryPayRule"
      - table: "employee_contract_leave_rules"
        join-on: "LoadingPayRule1"
      - table: "employee_contract_leave_rules"
        join-on: "LoadingPayRule2"
      - table: "employee_contract_leave_rules"
        join-on: "LoadingPayRule3"
      - table: "pay_rules"
        join-on: "Id"
      - table: "employee_contracts"
        join-on: "BasePayRule"
      - table: "employee_paycycle_returns"
      - table: "timesheet_pay_returns"

  - id: "roster-id"
    attribute: "Roster"
    table: "rosters"
    all-foreign-keys:
      - table: "roster_opens"
      - table: "roster_swaps"
        join-on: "SourceRoster"
      - table: "roster_swaps"
        join-on: "TargetRoster"
      - table: "rosters"
        join-on: "Id"
      - table: "timesheets"

  - id: "schedule-id"
    attribute: "Schedule"
    table: "schedules"
    all-foreign-keys:
      - table: "employee_availability"
      - table: "events"
      - table: "operational_units"
        join-on: "RosterActiveHoursSchedule"
      - table: "pay_rules"
      - table: "schedules"
        join-on: "Id"
      - table: "task_opunit_configs"
      - table: "task_setups"

  - id: "system-usage-balance-id"
    attribute: "BalanceId"
    table: "system_usage_balances"
    all-foreign-keys:
      - table: "system_usage_balances"
        join-on: "Id"
      - table: "system_usage_tracking"

  - id: "system-usage-tracking-id"
    attribute: "TrackingId"
    table: "system_usage_tracking"
    all-foreign-keys:
      - table: "system_usage_tracking"
        join-on: "Id"

  - id: "task-id"
    attribute: "Task"
    table: "tasks"
    all-foreign-keys:
      - table: "tasks"
        join-on: "Id"

  - id: "task-group-setup-id"
    attribute: "GroupSetupId"
    table: "task_group_setups"
    all-foreign-keys:
      - table: "task_group_setups"
        join-on: "Id"
      - table: "task_groups"
      - table: "task_setups"
        join-on: "GroupId"

  - id: "task-group-id"
    attribute: "GroupId"
    table: "task_groups"
    all-foreign-keys:
      - table: "task_groups"
        join-on: "Id"
      - table: "task_opunit_configs"
        join-on: "GroupId"
      - table: "tasks"

  - id: "task-opunit-config-id"
    attribute: ""
    table: "task_opunit_configs"
    all-foreign-keys:
      - table: "task_opunit_configs"
        join-on: "Id"

  - id: "task-setup-id"
    attribute: "TaskSetupId"
    table: "task_setups"
    all-foreign-keys:
      - table: "task_opunit_configs"
      - table: "task_setups"
        join-on: "Id"
      - table: "tasks"

  - id: "timesheet-id"
    attribute: "Timesheet"
    table: "timesheets"
    all-foreign-keys:
      - table: "leave_pay_lines"
        join-on: "TimesheetId"
      - table: "rosters"
        join-on: "MatchedByTimesheet"
      - table: "timesheet_pay_returns"
      - table: "timesheets"
        join-on: "Id"

  - id: "training-module-id"
    attribute: "Module"
    table: "training_modules"
    all-foreign-keys:
      - table: "training_modules"
        join-on: "Id"
      - table: "training_records"

---