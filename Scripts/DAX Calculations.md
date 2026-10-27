# Contents

- DAX USED for KPI's in the Measures_Table.
- DAX for creating Year-over-Year variable metrics in the Measures_Table.
- DAX for creating Year-over-Year variable metric's conditional color formating in the Measures_Table.
- DAX for Creating Dates_Table.

## DAX USED for KPI's in the Measures_Table

MaxOrderDate = MAX('Cleaned_E_Commerce'[Order Date])
MinOrderDate = MIN('Cleaned_E_Commerce'[Order Date])
Total_Customers = DISTINCTCOUNT('Cleaned_E_Commerce'[Customer ID])
Total_Sales = SUM('Cleaned_E_Commerce'[Sales])
AvgRecency = AVERAGE(RFM_E_Commerce[Recency])
AvgFrequency = AVERAGE(RFM_E_Commerce[Frequency])
AvgMonetary = AVERAGE(RFM_E_Commerce[Monetary])


## DAX for creating Year-over-Year variable metrics in the Measures_Table

YoY FrequencyVar = 
 VAR LY = CALCULATE([AvgFrequency], SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR LYFormatted = FORMAT(LY, "#,0.00")
 var yoyCalc = DIVIDE(([AvgFrequency] - LY) , LY)
 var yoyCalcFormatted = FORMAT(yoyCalc,"0.0%;(0.0%)")
 
RETURN
 SWITCH(
    True(),
    yoyCalc >0, UNICHAR(9650) & " " & yoyCalcFormatted & " | LY " & LYFormatted,
    ISBLANK(LY), UNICHAR(8211) & " | No Data for Last Year ",
    
    UNICHAR(9660) & " " & yoyCalcFormatted  & " | LY " & LYFormatted
 )


YoY MonetaryVar = 
 VAR LY = CALCULATE([AvgMonetary], SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR LYFormatted = FORMAT(LY/1000000, "$#,0") & "M"
 var yoyCalc = DIVIDE(([AvgMonetary] - LY) , LY)
 var yoyCalcFormatted = FORMAT(yoyCalc,"0.0%;(0.0%)")
 
RETURN
 SWITCH(
    True(),
    yoyCalc >0, UNICHAR(9650) & " " & yoyCalcFormatted & " | LY " & LYFormatted,
    ISBLANK(LY), UNICHAR(8211) & " | No Data for Last Year ",
    
    UNICHAR(9660) & " " & yoyCalcFormatted  & " | LY " & LYFormatted
 )


YoY RecencyVar = 
 VAR LY = CALCULATE([AvgRecency], SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR LYFormatted = FORMAT(LY, "#,0")
 var yoyCalc = DIVIDE(([AvgRecency] - LY) , LY)
 var yoyCalcFormatted = FORMAT(yoyCalc,"0.0%;(0.0%)")
 
RETURN
 SWITCH(
    True(),
    yoyCalc >0, UNICHAR(9650) & " " & yoyCalcFormatted & " | LY " & LYFormatted,
    ISBLANK(LY), UNICHAR(8211) & " | No Data for Last Year ",
    
    UNICHAR(9660) & " " & yoyCalcFormatted  & " | LY " & LYFormatted
 )
 
 
YoY SalesVariance = 
 VAR LY = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR LYFormatted = FORMAT(LY/1000000, "$#,0.00") & "M"
 VAR yoyCalc = DIVIDE([Total Sales] - LY, LY)
 VAR yoyCalcFormatted = FORMAT(yoyCalc, "0.0%; (0.0%)")

 RETURN
  SWITCH(
    TRUE(),
    yoyCalc > 0, UNICHAR(9650) & " " & yoyCalcFormatted & " | LY " & LYFormatted,
    ISBLANK(LY), UNICHAR(8211) & " | No Data for Last Year",
    yoyCalc = 0, UNICHAR(8211) & " | No Change from Last Year",
    UNICHAR(9660) & " " & yoyCalcFormatted & " | LY " & LYFormatted)


## DAX for creating Year-over-Year variable metric's conditional color formating in the Measures_Table  

FrequencyYoYColor = 
 VAR LY = CALCULATE([AvgFrequency],SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR YOY = DIVIDE([AvgFrequency] - LY ,LY)
 
RETURN
 SWITCH(TRUE(),
    YOY > 0, "#00B200", 
    OR(ISBLANK(LY), LY=0),"Orange", "#FF0000")


MonetaryYoYColor = 
 VAR LY = CALCULATE([AvgMonetary],SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR YOY = DIVIDE([AvgMonetary] - LY ,LY)
 
RETURN
 SWITCH(TRUE(),
    YOY > 0, "#00B200", 
    OR(ISBLANK(LY),LY=0),"Orange", "#FF0000")


RecencyYoYColor = 
 VAR LY = CALCULATE([AvgRecency],SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR YOY = DIVIDE([AvgRecency] - LY ,LY)
 
RETURN
 SWITCH(TRUE(),
    YOY > 0, "#00B200", 
    OR(ISBLANK(LY), LY = 0),"Orange", "#FF0000")


SalesYoYColor = 
 VAR LY = CALCULATE([Total Sales], SAMEPERIODLASTYEAR(Dates_Table[Date]))
 VAR YOY = DIVIDE([Total Sales] - LY, LY)

 RETURN
  SWITCH(TRUE(),
    YOY > 0, "#00B200",
    OR(ISBLANK(LY),LY=0), "Orange", "#FF0000")



## DAX for Creating Dates_Table

Dates_Table = 
ADDCOLUMNS (
    CALENDAR (MinOrderDate, MaxOrderDate), 
    "Year", YEAR([Date]),
    "Month Number", MONTH([Date]),
    "Month Name", FORMAT([Date], "MMMM"),
    "Year-Month", FORMAT([Date], "YYYY-MM"),
    "Quarter", "Q" & FORMAT([Date], "Q"),
    "Day", DAY([Date]),
    "Day of Week", WEEKDAY([Date], 2),   -- 1 = Sunday start, 2 = Monday start
    "Day Name", FORMAT([Date], "dddd"),
    "Week Number", WEEKNUM([Date], 2)
)



