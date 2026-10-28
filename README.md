# Power-BI-DAX-Data-Visualization
Combined the columns in 'order_details'  { Category_Type = 'Order Details(1)'[Category] &" "& 'Order Details(1)'[Sub-Category] }
Added a column named 'Revenue' {    Revenue = 'Order Details(1)'[Amount]*'Order Details(1)'[Quantity]  }
Added a column named Sales_Category   { Sales_Category = IF('Order Details(1)'[Revenue]>=AVERAGE('Order Details(1)'[Amount])," Above Average","Below Average") }
Calculate_order_count - {  Count_of_Orders = DISTINCTCOUNT('Order Details(1)'[Order ID])  }
Average_Profit_in_Delhi = CALCULATE(AVERAGE('Order Details(1)'[Profit]),'List of Orders(1)'[City]="Delhi")
CALENDAR = CALENDAR(MIN('List of Orders(1)'[Order Date]),MAX('List of Orders(1)'[Order Date]))  , YTD Sales = TOTALYTD([Total_Sales_Amount],'CALENDAR'[Date])
            I created the relationship between the tables from CALENDAR TO LIST_OF_ORDERS AS MANY TO ONE IN SINGLE
            ORDERS_DETAILS TO SALES_TARGET 'MANY TO MANY' same for ORDER_DETAILS TO LIST_OF ORDERS
       NOTE: it was automatically fixing as MANY TO MANY as i was doing for ONE TO MANY
  inserted CLUSTERED COLUMN - X AXIS :Category,Y-axis:Sum_target and Total_sales_target
  Inserted Donut Column - Legend :Sub_category,Values-Max_profit_Margin
  Inserted Line_chart - X axis :Date,Y_axis-Total_Sales_Amount
  Inserted Scatter chart -Values :Sub_category,X_Axis-Sum_of_profit,Y_axis-Sum_of_Quantity
  Inserted Multi-cards : first i made a MEASURE  for Minimum_sales_Target then added CATEGORY  and this measure to it also with TOTAL_SALES AND SUM OF SALES TARGET
  Inserted MATRIC and included TOTAL_SALES_AMOUNT ,MONTH_NAME AND CATEGORY
  Inserted MAP and LOCATION- CITY,BUBBLE SIZE & TOOLTIPS -TOTAL_SALES_AMOUNT 
  Inserted TREEMAP VALUES- TOTAL_SALES_AMOUNT AND CATEGORY- SUB_CATEGORY
  Inserted FUNNEL VALUES -ORDER_COUNT (ORDER_COUNT = DISTINCTCOUNT('List of Orders(1)'[Order ID]),CATEGORY-STATE
