
#  **PowerBI Naming Framework**

### The Manifesto
>This manifesto is a commitment to transforming **PowerBI** from a mere reporting tool into a governed engineering environment. My intention is to bridge the gap between raw data and decision-making by transitioning rigorous programming practices and clean code principles into the world of business intelligence.
>By moving away from "database-speak" and ad-hoc naming, we are building a unified, human-centric language that treats data models with the same architectural significance as a professional software product
> 
> *Nashat J. Omar*

### Release History:
>  - *Version 0.1 : Introduced the Framework* 
>  - *Version 0.2:  Naming Convention for Transformed Tables[Groupby,Summarize,Join, Calculate Table] and Calculated Columns* found under *[v0.2]*

 
### **Current Release** 
- **Current Version** :  *0.2*
-  **Date** : *February 2026*
- **Author** : *Nashat Jumaah Omar*
- Auther's LinkedIn: www.linkedin.com/in/nash-j
- Email : nashattt90@gmail.com



> ### **LICENSING AND ATTRIBUTION**
> 
> **Copyright © 2026 Nashat J. Omar**
> *Permission is hereby granted, free of charge, to any person obtaining
> a copy of this documentation to use, copy, modify, and distribute the
> standards without restriction, subject to the following conditions:*
> 
> 1.  **Copyright Notice:** *The above copyright notice and this permission notice shall be included in all copies or substantial portions of the document.*
> 2.  **Mandatory Reference:** *Any implementation, adaptation, or derivative work based on these standards must maintain an explicit reference to this original document. Attribution to the source and author must remain intact and clearly visible within the metadata or documentation of any project where this framework is applied.*
> 3.  **Commercial and Internal Use:** *Permission is granted for the framework to be used within commercial organizations for internal project governance and dashboard development. However, the sale, sub-licensing, or commercial redistribution of the Framework itself as a standalone product or consulting framework is strictly prohibited without written consent from the author.*


## **Table of Content:** 

1. [Introduction to the Manifesto](#1-introduction-to-powerbi-naming-convention-manifesto)
2. [Main Convention Rules](#2-main-convention-rules)
3. [Measures](#3-measures)
4. [Tables](#4-tables)
5. [Columns](#5-columns)
6. [References](#6-refrences)

## **1-Introduction to PowerBI Naming Conventions**

###  The Reason for Naming
Data is only as powerful as it is understandable. In the world of Power BI, names are not just labels; they are the **bridge** between engineering logic and clear business decisions, names are used indirectly to drive insights, we might not see them, but they are playing an important role to the dashboarding creator/maintainer.
This manifesto exists to insure adherence to :

### 1. Unified Language Across the Team
 It ensures that whether a colleague is looking at the DAX code or a manager is looking at a chart, they never have to guess what they are seeing. Clarity is our greatest act of collaboration.

### 2. Eliminating the Guess Work
The structural integrity of a data model is reflected in its nomenclature. Standardizing our naming conventions transitions the workspace from a collection of disparate calculations into a governed, enterprise-grade analytical asset, which will eventually drive Logical Transparency, Quality, Standardized Practice.
A messy model with "Column 1" and "Measure (2)" signals a messy and fragile data analysis and dashboarding process. By using structured naming, we prioritize our data models. Clean naming is a reflection of clean thinking; this will potentially save time to personals doing maintenance work on the dashboards.

### 3. To Build for the Future
A standardized naming convention ensures that intellectual property remains accessible long after the initial development phase. Future developers—including our future selves—should not have to "reverse-engineer" the intent behind a calculation. Clear, standard nomenclature serves as immediate documentation, allowing the focus to remain on solving business problems rather than deciphering technical debt.

## **2-Main Convention Rules**
1. This Manifesto uses a combination of **PascalCasing** for internal data handling logic and **Natural Language presentation**  for visualization and high-level perception of the dashboarding elements.
2. **PascalCasing** is the practice of writing compound words or phrases such that each word in the phrase begins with a capital letter, with no intervening spaces or punctuation.
3. **PascalCasing** shouldn't start with small casing letters `(a-z)`:   `Bad :   oilRateAverage`  `Correct :  OilRateAverageMonthly`
4. Object names must be descriptive, relevant, resonates with overall business orientation of the dashboarding and clearly indicates the goal of the calculation.
`Bad Example : QOAv`
`Correct Example : GORAverageMonthly`
6. Object names must start with an uppercase letter`(A-Z)`. This distinguishes objects (Tables/Measures) from variables or lower-level DAX elements (internal variables).
7. Data Lineage : Tables, column names that are being imported from SQL, Access, Excel or any record management system(RMS) should stay intact and unchanged, to insure traceability.
8. Object Names shouldn't start with numbers `(0 - 9)` or special Characters `(#,$,%,^,&)` .[Objects include the building blocks of a data model: Measures, Tables, Columns, Relationships]
9. Spaces shouldn't be usedwithin object name to seperate words, this will make retrieving and using object names unnatural and error prone.If the object name is made up of one syllable or more, always adhere to the PascalCasing.
	**Examples :** 
	*Bad Names* :  `OilRate, GasRate, GasOilRatio`
	*Good Names:*   `oilrate, gasRATE,  GASoilRAtio`
10. Use Standardized English Language (Either US or UK), don't intermix the two 
` Example :  Don't Mix   Meter(US) and Metre(UK)`
11. Use Mono Language Only (English, Arabic, Spanish, Turkish, Italian, etc).For Visuals other languages can be used for clarity and context.
12. When possible, it's highly recommended to stick to English as main language of naming, this is for technical precision, avoiding special encoding issues and improved searchability

13. **Right to Left Script** * **Characters:** `أ, ب, ت, ج, د, ر, ز, س ...`  **Source:** Arabic / Farsi / Urdu  **Risk:** Causes "Cursor Jumping" in the DAX formula bar; mixes Right-to-Left and Left-to-Right logic, making complex formulas impossible to debug.
14. **Spanish & Latin Accents** : `ñ, Ñ, á, é, í, ó, ú, ü` * **Source:** Spanish / French / Portuguese    **Risk:** These characters can cause "Table Not Found" errors when the model is queried by Python scripts or external APIs that expect standard UTF-8 or ASCII alphanumeric strings.
   


## **3-Measures**

 1. All Clauses listed in Section.2 are applicable.
 2. All Measures should explicitly show the aggregation process clearly in the name, an example on using `SUM()` to calculate Oil Rate Total  : `good : OilVolumeTotal  bad : OilVol`   stating the aggregation in the name helps eliminating ambiguity : `Good: WellheadPressureAverage  Bad : WellheadP`
 3. **Explicit Aggregation Naming :** Aggregation and Statistical Description should be used as  a suffix, avoid using them as prefixes   `Good : WellheadTemperatureMax    Bad :  MaxWellheadTemperature` this will allow easier search for objects
 4.  A level of object hierarchy should be implemented for naming purposes such  as    **Parameter->Detail->Aggregation**  example on parameters : `(Oil, Gas, Water, Pressure, Temperature, Sales)`, examples on Details: `(Export, Shut-in, Opening, Commissioning)` examples on Aggregation: `(Total, Max, Min, Last, First)`  
  `Examples  PressureShutinMax,    OilExportTotal,  GasFlaredMax`
 5. Variables within measures should be treated with a prefix underscore `_` to denote private variable while maintaining **PascalCasing**.
 `VAR  _OilRate = 15000`
 6. **Time Intelligence** : If a measure implements a form of DateTime manipulation, the measure name should indicate the time grain used. 
  `Format :  [Parameter][Detail][Aggregation][Time]`
  `Time Suffixes :  YTD, YoY, MoM QoQ`
 `Examaple :  OilExportDifferalYoY`
  7. **Unit of Measure|Column**[Optional]: For engineering or financial data where units might change (e.g., Barrels vs. Standard Cubic Feet).The unit should be separated by underscore  `_`  towards the end of the measure or column name.
 `Example :  GasVolumeTotal_MSCF`
 7. Characters in a single measure name shouldn't exceed 35 characters (including white spaces and underscores `_`)
 8. Length of a given measure name shouldn't exceed `35` characters to increase visibility, minimize Data Pane footprint and minimize time spent on Data Pane Resizing.
 9. Nonobvious calculation logic should be documented with `//` docstrings or by filling out the description box in Model View
 10. *[v0.2]* Measures should be documented as early as possible [prefereabiliy after writing off the measure and proving its functionality] 
 11.  *[v0.2]* Bellow measure documentation template can be implemented at the top of the measure. Each Updated On entry should correspond with an Employee Name/Email set, the count of updated on entry should equal to updated by entries 

> // Purpose : Calculates total fluid volume using Banker's Rounding to minimize statistical bias. 
> // Created On : 2026-01-15
> // Updated On : 2024-02-01,   2025-02-15
> // Author : [Jack Doe / jdoe@corp.net ]  
> //Updated By : [Jack Doe / jdoe@corp.net ], [Joly Fords / jfords@corp.net ]  

   
## **4-Tables**
 1. All Clauses in Section.2 are applicable
 2. **Fact Tables** are business tables that contains data that gets updated with time or business processes. Newly created tables can be prefixed with the word `Fact` to distinguish it from other types.
`Example : FactProductionDaily`
`Example : FactSalesYearly`
 3. Descriptive Dimensional table should be prefixed with `Dim`, these table contains data with minimal updates
 `Example :  DimEquipments`
 `Example :  DimGeologicalFormations`
 4. Singular name should be used for tables
`Example :   Well   not  Wells`
 5. **Context Suffix**: If a table has an update frequency like `Daily`, 		`Hourly`, etc., this should be stated clearly 
`Example : FactInjectionMoldVolumeHourly`
`Bad Example : FactInjection !  is this monthly? hourly?`
 6. **Transformed, Manipulated and Raw tables**: Table that undergoes intensive manipulation and transformation, should be indicated by a suffix `Clean`  , `Raw`  , `Imputed` 
`Example :   FactProductionMonthlyTotalClean`
 7. *[v0.2]* Tables that are product of joining two tables should specify that clearly in the name of newly generated table. The following naming pattern should be followed:    `LeftRightJoinTypeJoin` examples :   `Left Table :  Well` , `Right Table : Cluster` , `Join Type : InnerJoin` the name would be :  `WellClusterIJJoin` 
 8. *[v0.2]* Join types can be shortened to keep the name of the column short enough the followings are recommended :   ` Inner Join : IJ`, `Outer Join : OJ`, `Cross Join : CJ` 
 9. *[v0.2]* Tables that under go `SUMMARIZE()` should clearly state that in the table name `EquipmentLocationSummarized`
 10. *[v0.2]* Tables that under go `GROUPBY()` should clearly state that in the table name :  `SensorGroupbyLocation`
 11. *[v0.2]* Tables that are generated by `CALCULATETABLE`, `FILTER` or any other function that reduces the effective number of retrieved rows(alteration in filtercontext) should be ended with `SubSet` Suffix. Example : `Raw Table :  ProductionEntit`  -> `View Table ProductionEntitySubset` 
 12. *[v0.2]* Tables that return more columns than it's original raw tables using `ADDCOLUMNS()` should be suffixed with `Extd`  or `Extended` Example : `EquipmentExtd` or `EquipmentExtended`
 13. *[v0.2]* Clause 3.11 should be applied if Calculated columns have complex enough logic
 14. Length of a given table name shouldn't exceed `20` characters to    
    increase visibility, minimize Data Pane footprint and fit most of
    the    name in the default Data Pane allocated area(Not applicable
    on       Ultra-wide screens).
  
  
## **5-Columns**
1. All Clauses from Section.2 Applies to the Columns: Original and Calculated.
2. Clause `8` and`9`  in  Section `3` is applicable.
3. Avoid Having Calculated Columns in Calculated table to decrease memory footprint.
4. Name of Columns that Return binary results (0, 1) or (True, False) should start with the words `Is` or `Has` 
`Example :  IsProducing`
`Example : HasESP`
5. For Safe calculations in Calculated columns avoid using `/` use `DIVIDE()` function instead which has `Division By Zero` logic in place.
6. Encapsulation Protocols: Columns that hold Key data (Foreign, Primary, Surrogate) or Ranking Columns can be prefixed with underscore `_` to signal developers that these are structural components with no analytical significance.
`Example : _WellNameKeyID, _GeoColumnFmNameID`
7. *[v0.2]* BI Developers are encouraged to use `_` underscore as a preffix to column names that are used as intermediate calculation more known as **`Shadow Columns`**.Example :  `_CurrentMonthInt` can be used as shadow column for a final column `ProductionMonthlyGrouped`
8. *[v0.2]* **Shadow Columns** should be hidden from the data model(using PowerBI interface)
9. *[v0.2]* Calculated Columns with mathematical rounding in place(with potential lose of precision) should state that explicitly by using `BRound` , `FRound`, `CRound`Suffixes corresponding to Banker's rounding, Floor Rounding, Ceiling Round Example:  `TotalFluidBRound`, `TotalFluidFRound`
10. Always format columns for Date and Numeric representation


## **6-Refrences**

-   **Clean Code & Meaningful Names:** Clean Code Book by Robert C. Martin (Uncle Bob)
- **PascalCasing & Object Identification:** [Microsoft Developer Guidelines (https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/capitalization-conventions)
-   **Dimensional Modeling (Fact & Dim):** 
	- [Fact table - Wikipedia](https://en.wikipedia.org/wiki/Fact_table)
	- [Dimension table - Wikipedia](https://en.wikipedia.org/wiki/Dimension_(data_warehouse)#Dimension_table)
    
-   **Semantic Layer Governance:** [DAMA International (DMBOK)](https://www.dama.org/cpages/body-of-knowledge)

-   **Variable Scoping (_):** [Microsoft .NET Coding Conventions](https://learn.microsoft.com/en-us/dotnet/csharp/fundamentals/coding-style/coding-conventions) 
-   **DAX Best Practices:** [SQLBI Naming Standards](https://www.sqlbi.com/articles/rules-for-dax-code-formatting/)
