#  **PowerBI Naming Manifesto**

**Table of Content:**
	1.Introduction to the Manifesto
	
	2.Main Convention Rules
	
	3.Meausres
	
	4.Tables
	
	5.Columns
	


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
4. Spaces are not allowed within objects. If the object name is made up of two syllable, you should adhere to the PascalCasing.

	**Examples :** 
	*Allowed Names* :  OilRate, GasRate, GasOilRatio
	*Not Allowed:*   oilrate, gasRATE,  GASoilRAtio
	



## **3-Measures**

 1. All Rules listed in section #2 is applicable.
 2. All Measures should explicitly show the aggregation process clearly in the name  an example on using SUM() to calculate Oil Rate Total  : `good : TotalOilVolume  bad : OilVol`   stating the aggregation in the name helps eliminating ambiguity : `good: AverageWellheadPressure  bad : WellheadP`
 3. 
