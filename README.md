This function implements the Pareto (80/20) principle for customers based on a given KPI (for example, Sales, Revenue, or Profit).

For the currently selected customer, the function:

1.Calculates the KPI value for all customers in the current filter context.
2.Ranks customers by their KPI contribution.
3.Computes the cumulative contribution across customers, starting from the highest contributor.
4.Determines whether the current customer falls within the top X% (default 80%) of the total KPI value.

The function returns:
- 1 if the customer is part of the top Pareto group (i.e. contributes to the first X% of total KPI value).
- 0 if the customer falls outside of that group.
- BLANK() when the calculation is not applicable (for example, when no customer is in context).

Typical usage scenarios:

1. Apply the function as a visual-level or page-level filter (= 1) to show only top-contributing customers.
2. Use it in measures to conditionally include or exclude customers from calculations.
3. Combine it with conditional formatting to highlight Pareto customers in tables and matrices.

Example:
1. Create a measure: 
Is Top 80% Customer :=
fn_ParetoTopCustomers( [Total Sales], 0.8 )

2. Then filter visuals to:
Is Top 80% Customer = 1

Important notes:
- The function is KPI-agnostic. It works with any numeric measure passed as input.
- The Pareto threshold is configurable via the Pct parameter (for example, 0.8 for 80%).
- Because it returns a flag, it is designed to be used as a filter, not as a displayed metric. Only rows where the function returns 1 should be used.
