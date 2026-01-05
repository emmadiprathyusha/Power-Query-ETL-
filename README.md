Problem Statement

The source Excel file had:
	•	Headers spread across multiple rows
	•	Shipping Mode and Segment values stored as column headers
	•	Order ID and Order Date mixed with metadata
	•	Sales values scattered across multiple columns
	•	No direct way to promote headers

This structure made the data unusable for analytics or Power BI modeling.

⸻

🛠 Tools Used
	•	Microsoft Excel
	•	Power Query


⸻

🔄 Data Transformation Steps (Power Query)

1️⃣ Load Data into Power Query
	•	Loaded raw Excel sheet into Power Query
	•	Kept default column names (Column1, Column2, etc.)
	•	Avoided promoting headers initially

⸻

2️⃣ Remove Empty & Metadata Rows
	•	Filtered out rows containing only null
	•	Isolated rows related to:
	•	Ship Mode
	•	Segment
	•	Order ID
	•	Order Date

⸻

3️⃣ Create a Header Helper Query
	•	Duplicated the base query
	•	Kept only header-related rows
	•	Removed transaction rows
	•	Transposed the table to align headers horizontally

⸻

4️⃣ Build Dynamic Headers
	•	Combined Ship Mode + Segment values (e.g., First Class Consumer)
	•	Preserved Order ID and Order Date
	•	Converted the final header row into a list
  
6️⃣Apply Headers to Main Table
	•	Returned to the main data query
	•	Removed metadata rows
	•	Used List.Zip + Table.RenameColumns to apply headers programmatically
  
6️⃣ Unpivot Sales Columns
	•	Unpivoted Ship Mode + Segment columns
	•	Converted wide format → long format
	•	Created clean columns:
	•	Ship Mode
	•	Segment
	•	Sales

⸻

7️⃣ Final Cleanup
	•	Renamed columns for clarity
	•	Set correct data types
	•	Removed unnecessary null values

⸻

✅ Final Output

The cleaned dataset contains:
	•	Order ID
	•	Order Date
	•	Ship Mode
	•	Segment
	•	Sales Amount
