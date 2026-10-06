BEGIN PROGRAM

    // Initialize income category totals
    SET designIncome = 0
    SET codingIncome = 0
    SET documentationIncome = 0

    // Initialize expense category totals
    SET softwareExpense = 0
    SET equipmentExpense = 0
    SET workspaceExpense = 0

    // Main loop
    REPEAT

        DISPLAY "=========================================="
        DISPLAY "      PERSONAL BUDGET TRACKER             "
        DISPLAY "=========================================="
        DISPLAY ""
        DISPLAY "--- MAIN MENU ---"
        DISPLAY "1. Log Income"
        DISPLAY "2. Log Expense"
        DISPLAY "3. View Financial Summary"
        DISPLAY "4. Exit"
        DISPLAY "Enter your choice (1-4): "

        INPUT choice

        // Validate main menu choice
        WHILE choice < 1 OR choice > 4
            DISPLAY "Invalid. Choice must be 1, 2, 3, or 4. Try Again:"
            INPUT choice
        END WHILE

        // Option 1: Log Income
        IF choice == 1 THEN

            DISPLAY ""
            DISPLAY "--- INCOME MENU ---"
            DISPLAY "1. Design"
            DISPLAY "2. Coding"
            DISPLAY "3. User Documentation"
            DISPLAY "Enter income category:"

            INPUT incomeCategory

            // Validate income category
            WHILE incomeCategory < 1 OR incomeCategory > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT incomeCategory
            END WHILE

            DISPLAY "Enter income amount ($):"
            INPUT incomeAmount

            // Validate income amount
            WHILE incomeAmount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT incomeAmount
            END WHILE

            // Add income to correct category
            IF incomeCategory == 1 THEN
                designIncome = designIncome + incomeAmount
                DISPLAY "Successfully added $", incomeAmount, " for Design."
            ELSE IF incomeCategory == 2 THEN
                codingIncome = codingIncome + incomeAmount
                DISPLAY "Successfully added $", incomeAmount, " for Coding."
            ELSE
                documentationIncome = documentationIncome + incomeAmount
                DISPLAY "Successfully added $", incomeAmount, " for User Documentation."
            END IF

        END IF

        // Option 2: Log Expense
        IF choice == 2 THEN

            DISPLAY ""
            DISPLAY "--- EXPENSE MENU ---"
            DISPLAY "1. Software"
            DISPLAY "2. Equipment"
            DISPLAY "3. Workspace"
            DISPLAY "Enter expense category:"

            INPUT expenseCategory

            // Validate expense category
            WHILE expenseCategory < 1 OR expenseCategory > 3
                DISPLAY "Invalid. Please enter 1, 2, or 3. Try Again!"
                INPUT expenseCategory
            END WHILE

            DISPLAY "Enter expense amount ($):"
            INPUT expenseAmount

            // Validate expense amount
            WHILE expenseAmount < 0
                DISPLAY "Invalid. Please enter amount >= 0:"
                INPUT expenseAmount
            END WHILE

            // Add expense to correct category
            IF expenseCategory == 1 THEN
                softwareExpense = softwareExpense + expenseAmount
                DISPLAY "Successfully added $", expenseAmount, " for Software."
            ELSE IF expenseCategory == 2 THEN
                equipmentExpense = equipmentExpense + expenseAmount
                DISPLAY "Successfully added $", expenseAmount, " for Equipment."
            ELSE
                workspaceExpense = workspaceExpense + expenseAmount
                DISPLAY "Successfully added $", expenseAmount, " for Workspace."
            END IF

        END IF

        // Option 3: View Financial Summary
        IF choice == 3 THEN

            SET totalIncome = designIncome + codingIncome + documentationIncome
            SET totalExpenses = softwareExpense + equipmentExpense + workspaceExpense
            SET netBalance = totalIncome - totalExpenses

            DISPLAY "=========================================="
            DISPLAY "          FINANCIAL SUMMARY               "
            DISPLAY "=========================================="
            DISPLAY "Total Income:   $", totalIncome
            DISPLAY "Total Expenses: $", totalExpenses
            DISPLAY "Net Balance:    $", netBalance

            IF netBalance > 0 THEN
                DISPLAY "Status: You are profitable this month!"
            ELSE IF netBalance < 0 THEN
                DISPLAY "Status: You are losing money this month."
            ELSE
                DISPLAY "Status: You broke even this month."
            END IF

            DISPLAY "=========================================="

        END IF

    UNTIL choice == 4

    DISPLAY "Thank you for using Personal Budget Tracker. Goodbye!"

END PROGRAM
