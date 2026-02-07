#  **PowerBI Naming Manifesto**

 - **Version** :  *0.1*
 -  **Date** : *February 2026*
 - **Author** : *Nashat Jumaah Omar*
 -  [Auther's LinkedIn](www.linkedin.com/in/nash-j)
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
> **Commercial and Internal Use:** *Permission is granted for the framework to be used within commercial organizations for internal project governance and dashboard development. However, the sale, sub-licensing, or commercial redistribution of the Framework itself as a standalone product or consulting framework is strictly prohibited without written consent from the author.*

> **THE DOCUMENTATION IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED.**

**Table of Content:**

 1. 1.Introduction to the Manifesto 
 2. Main Convention Rules
 3. Measures
 4. Tables
 5. Columns

## **1-Introduction to PowerBI Naming Convention Manifesto**

###  The Reason for Naming
Data is only as powerful as it is understandable. In the world of Power BI, names are not just labels; they are the **bridge** between engineering logic and clear business decisions, names are used indirectly to drive insights, we might not see them, but they are playing an important role to the dashboarding creator/maintainer.
This manifesto exists to insure adherence to :

### 1. Unified Language Across the Team
 It ensures that whether a colleague is looking at the DAX code or a manager is looking at a chart, they never have to guess what they are seeing. Clarity is our greatest act of collaboration.

### 2. Eliminating the Guess Work
The structural integrity of a data model is reflected in its nomenclature. Standardizing our naming conventions transitions the workspace from a collection of disparate calculations into a governed, enterprise-grade analytical asset, which will eventually drive Logical Transparency, Quality, Standardized Practice.
A messy model with "Column 1" and "Measure (2)" signals a messy and fragile data analysis and dashboarding process. By using structured naming, we prioritize our data models. Clean naming is a reflection of clean thinking, this will potentially save time to personals doing maintenance work on the dashboards.

### 3. To Build for the Future
A standardized naming convention ensures that intellectual property remains accessible long after the initial development phase. Future developers—including our future selves—should not have to "reverse-engineer" the intent behind a calculation. Clear, standard nomenclature serves as immediate documentation, allowing the focus to remain on solving business problems rather than deciphering technical debt.

## **2-Main Convention Rules**
1. This Manifesto Uses a combination of **PascalCasing** for internal data handling logic and **Natural Language presentation**  for visualization and high level perception of the dashboarding elements.
2. Data Lineage : Any table, column names that are being imported from SQL, Access, Excel or any record management system should stay intact and unchanged this will insure traceability.
3. Object Names shouldn't start with Numbers(0 - 9), Special Characters (#,$,%,^,&).[Objects include the building blocks of a data model : Measures, Tables, Columns, Relationships]

4. Spaces are not allowed within object name, this will make retrieving and using names unnatural and error prone. If the object name is made up of two syllable, you should adhere to the PascalCasing.

	**Examples :** 
	*Allowed Names* :  OilRate, GasRate, GasOilRatio
	*Not Allowed:*   oilrate, gasRATE,  GASoilRAtio
5. Use Standardized English Language (Either US or UK), don't intermix the two 
` Example :  Don't Mix   Meter(US) and Metre(UK)`
6. Use Mono Language Only (English, Arabic, Spanish, Turkish, Italian, etc).For Visuals other languages can be used for clarity and context.
7. When possible, it's highly recommended to stick to English as main language of naming, this is for technical precision, avoiding special encoding issues and improved searchability

8. **Right to Left Script** * **Characters:** `أ, ب, ت, ج, د, ر, ز, س ...`  **Source:** Arabic / Farsi / Urdu  **Risk:** Causes "Cursor Jumping" in the DAX formula bar; mixes Right-to-Left and Left-to-Right logic, making complex formulas impossible to debug.
9. **Spanish & Latin Accents** : `ñ, Ñ, á, é, í, ó, ú, ü` * **Source:** Spanish / French / Portuguese    **Risk:** These characters can cause "Table Not Found" errors when the model is queried by Python scripts or external APIs that expect standard UTF-8 or ASCII alphanumeric strings.
   


## **3-Measures**

 1. All Clauses listed in Section.2 is applicable.
 2. All Measures should explicitly show the aggregation process clearly in the name, an example on using SUM() to calculate Oil Rate Total  : `good : OilVolumeTotal  bad : OilVol`   stating the aggregation in the name helps eliminating ambiguity : `good: WellheadPressureAverage  bad : WellheadP`
 3. **Explicit Aggregation Naming :** Aggregation and Statistical Description should be used as  a suffix, avoid using them as prefixes   `good : WellheadTemperatureMax    bad :  MaxWellheadTemperature` this will allow easier search for objects
 4.  A level of object hierarchy should be implemented for naming purposes such  as    **Parameter->Detail->Aggregation**  example on parameters : (Oil, Gas, Water, Pressure, Temperature, Sales), examples on Details : (Export, Shut-in, Opening, Commissioning) examples on Aggregation : (Total, Max, Min, Last, First)  
  `examples  PressureShutinMax,    OilExportTotal,  GasFlaredMax`
 5. Variables within measures should be treated with a prefix underscore to denote private variable   
 `VAR  _OilRate = 15000`
 6. **Time Intelligence** : If a measure implements a form of DateTime manipulation, the measure name should indicate the time grain used. 
  `Format :  [Parameter][Detail][Aggregation][Time]`
  `Time Suffixes :  YTD, YoY, MoM QoQ`
  7. **Unit of Measure**[Optional]: For engineering or financial data where units might change (e.g., Barrels vs. Standard Cubic Feet).The unit should be separated by underscore  `_` 
 `Example :  GasVolumeTotal_MSCF`

   
## **4-Tables**
1. All Clauses in Section.2 is applicable
2. Fact Tables are business tables that contains data that gets updated with time or business processes. Newly created tables can be prefixed with the word `Fact` to distinguish it from other types.
`Example : FactProductionDaily`
` Example : FactSalesYearly`
3. Descriptive Dimensional table should be prefixed with `Dim`, these table contains data with minimal updates
 `Example :  DimEquipments`
 `Example :  DimGeologicalFormations`
4. Singular name should be used for tables
`Example :   Well   not  Wells`
5. **Context Suffix**: If a table has an update frequency like `Daily`, 		`Hourly`, etc., this should be stated clearly 
`Example : FactInjectionMoldVolumeHourly`
`Bad Example : FactInjection !  is this monthly? hourly?`
6. **Transformed, Manipulated and Raw tables**: Table that undergoes intensive manipulation and transformation, should be indicated by a suffix `Clean`  , `Raw`  , `Imputed` 
`Example :   FactProductionMonthlyTotal_Clean`
  
## **5-Columns**
1. All Clauses from Section.2 Applies to the Columns : Original and Calculated.
2. Avoid Having Calculated Columns in Calculated table to decrease memory footprint.
3. Name of Columns that Return binary results (0, 1) or (True, False) should start with the words `Is` or `Has` 
`Example :  IsProducing`
`Example : HasESP`
4. For Safe calculations in Calculated columns avoid using `/` use `DIVIDE()` function instead which has `Division By Zero` logic in place.
5. Always format columns for Date and Numeric representation.
