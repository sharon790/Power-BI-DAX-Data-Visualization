# Power-BI-DAX-Data-Visualization
Combined the columns in 'order_details'  { Category_Type = 'Order Details(1)'[Category] &" "& 'Order Details(1)'[Sub-Category] }
Added a column named 'Revenue' {    Revenue = 'Order Details(1)'[Amount]*'Order Details(1)'[Quantity]  }
Added a column named Sales_Category   { Sales_Category = IF('Order Details(1)'[Revenue]>=AVERAGE('Order Details(1)'[Amount])," Above Average","Below Average") }
