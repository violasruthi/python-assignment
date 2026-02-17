# python-assignment
1.
# STEP 1: Get inputs
annual_salary = float(input("Enter your annual salary: "))
portion_saved = float(input("Enter the percent of your salary to save, as a decimal: "))
total_cost = float(input("Enter the cost of your dream home: "))

# STEP 2: Calculate down payment (25% of total cost)
down_payment = 0.25 * total_cost

# STEP 3: Initialize savings
current_savings = 0.0
monthly_salary = annual_salary / 12  # Monthly income
monthly_saving = portion_saved * monthly_salary  # Monthly savings
r = 0.04 / 12  # Monthly return rate (4% annual)

# STEP 4: Calculate months needed
months = 0
while current_savings < down_payment:
    # Each month: Add savings + investment return
    current_savings += monthly_saving + (current_savings * r)
    months += 1

# STEP 5: Print result
print(f"Number of months: {months}")
2.
# STEP 1: Get all inputs
annual_salary = float(input("Enter your starting annual salary: "))
portion_saved = float(input("Enter the percent of your salary to save, as a decimal: "))
total_cost = float(input("Enter the cost of your dream home: "))
semi_annual_raise = float(input("Enter the semi-annual raise, as a decimal: "))

# STEP 2: Calculate down payment needed
down_payment = 0.25 * total_cost

# STEP 3: Initialize variables
current_savings = 0.0
monthly_salary = annual_salary / 12  # Current monthly salary
monthly_saving = portion_saved * monthly_salary
r = 0.04 / 12  # Monthly return rate
months = 0

# STEP 4: Simulate month-by-month savings
while current_savings < down_payment:
    # Add monthly savings + investment return
    current_savings += monthly_saving + (current_savings * r)
    months += 1
    
    # Apply semi-annual raise every 6 months
    if months % 6 == 0:
        annual_salary += annual_salary * semi_annual_raise
        monthly_salary = annual_salary / 12
        monthly_saving = portion_saved * monthly_salary

# STEP 5: Print result
print(f"Number of months: {months}")

3.
# STEP 1: Get input
annual_salary = float(input("Enter the starting salary: "))

# STEP 2: Bisection search setup
total_cost = 1000000
down_payment = 0.25 * total_cost  # $250,000
low = 0.0
high = 1.0  # Max 100% savings rate
steps = 0
epsilon = 100  # $100 accuracy
found = False

# STEP 3: Bisection loop
while high - low >= 1e-6:  # High precision
    steps += 1
    mid_rate = (low + high) / 2
    
    savings = calculate_savings (mid_rate, annual_salary)
    
    if abs(savings - down_payment) <= epsilon:
        print(f"Best savings rate: {mid_rate:.4f}")
        print(f"Steps in bisection search: {steps}")
        found = True
        break
    elif savings < down_payment:
        low = mid_rate
    else:
        high = mid_rate

# STEP 4: Impossible case check
if not found:
    # Test with 100% savings
    max_savings = calculate_savings (1.0, annual_salary)
    if max_savings < down_payment:
        print("It is not possible to pay the down payment in three years.")
    else:
        print(f"Best savings rate: {mid_rate:.4f}")
        print(f"Steps in bisection search: {steps}")


