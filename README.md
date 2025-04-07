

## **Workbook Summary: Key Points**  

---
 ## ** Week 1 Excell**
### **Day 1: Data Protection Laws**  
**Task 1: Compliance Overview**  
- **Data Protection Act (DPA)**:  
  - *What*: Regulates personal data handling to protect privacy.  
  - *Importance*: Ensures lawful, secure, and transparent data use.  
  - *Example*: Encrypting customer databases.  
  - *Impact*: Requires strict data management protocols.  
  - *Breach Consequence*: Fines, legal action, reputational damage.  

- **GDPR**:  
  - *What*: EU law for data privacy/security.  
  - *Example*: Obtaining explicit consent for marketing emails.  
  - *Breach Consequence*: Fines up to €20M or 4% of global revenue.  

- **Freedom of Information Act (FOIA)**:  
  - *What*: Public access to government-held data.  
  - *Example*: Citizens requesting NHS spending reports.  

- **Computer Misuse Act**:  
  - *What*: Criminalizes unauthorized system access.  
  - *Example*: Prosecuting hackers stealing customer data.  

---

### **Day 2: Excel Data Analysis**  
**Task 1: Basic Functions**  
1. **Convert to Table**: Organized data in columns A–J.  
2. **Age Filter**: Sorted ages largest to smallest.  
3. **SUM Function**: Total commission calculated in cell L10.  
4. **AVERAGE Function**: Average commission in cell L11.  
- *Screenshots missing* – Ensure these are added for submission.  


### **Day 3: Pivot Tables & Data Categorization**  
**Task 1: Bike Sales Pivot Table**  
- **Key Findings**:  
  - Germany serves customers in North America, Europe, and the Pacific.  
  - Australia has sales in all markets.  
  - Most profitable markets: Middle-aged males in the USA.  

**Task 2: Sales Performance Analysis**  
- **Pivot Table**: Summarized sales by county (rows) and product (columns).  
  - Example: Yorkshire sold 500 laptops, 200 smartphones.  
- **SWITCH Function**: Categorized sales volume:  
  - `=SWITCH(TRUE, C2 > 600, "High", C2 >= 300, "Medium", "Low")`.  
  - Results: Cornwall laptops = "High", Durham printers = "Low".  

**Task 3: Bike Sales Visualizations**  
- *Screenshot missing* – Likely included charts (e.g., bar graphs, pie charts) to show sales trends by demographics.  

---

### **Day 4: Presentation Preparation**  
**Task 1: Board Delivery Strategy**  
1. **Preparation**:  
   - Analyze churn data (e.g., 12-month renewal drop-off).  
   - Use tools like Excel, Power BI, or Tableau for visuals.  
2. **Prospecting**:  
   - Research customer pain points at renewal (e.g., surveys, feedback).  
3. **Public Speaking Tips**:  
   - Be concise, use data storytelling, rehearse, and anticipate questions.  
4. **Board Delivery**:  
   - Show churn trends, renewal pricing impact, and competitor comparisons.  
   - Recommend loyalty incentives or price adjustments.  
5. **Visualization Tools**:  
   - **Power BI/Tableau**: Interactive dashboards.  
   - **Excel**: Simple charts.  
   - **Canva**: Sleek slides.  

---

## ** Week 2 Tableau and Power BI **

## **Workbook Summary: Key Points**

### **Day 1: Tableau Overview**
- **Task 1: Tableau Versions Comparison**  
  - **Tableau Desktop**: Full analytics tool for creating dashboards; connects to databases, cloud services, Excel, etc.  
  - **Tableau Server/Cloud**: Enterprise platforms for secure collaboration; Server is self-hosted, Cloud is Tableau-managed.  
  - **Tableau Public**: Free but limited:  
    - Only connects to Excel/CSV/Google Sheets.  
    - All data/dashboards are public.  
    - No scheduled data refreshes or advanced features.  

- **Task 2: EMSI Job Change Dashboard**  
  - *Objective*: Create a bar chart (% job change) and UK map (impacted cities).  
  - *Screenshot missing* – Ensure visualizations are added for submission.

---

### **Day 2: Data Analysis**  
- **Task 1: Spotify Trends**  
  - **Key Findings**:  
    1. **Popularity & Duration**: Longer songs trend toward higher popularity.  
    2. **Danceability**: Reggaeton/Hip-Hop are top genres for danceable tracks.  
    3. **Energy Levels**: Ska, Reggaeton, and Rock have high energy.  
    4. **Top Genres**: Pop, Rap, and Rock dominate popularity.  
  - **Implications**:  
    - Artists should focus on danceable, high-energy tracks for mainstream success.  
    - Streaming platforms can optimize playlists using these metrics.  

- **Task 2: Health Data & NHS Applications**  
  - **Key Insights**:  
    1. **Life Expectancy**: Rising globally but disparities exist (Africa lags behind Europe/Americas).  
    2. **Health Indicators**: Higher BMI/cholesterol correlate with higher life expectancy (likely due to healthcare access).  
  - **NHS Recommendations**:  
    - Target preventative care for men (lower life expectancy).  
    - Address regional inequalities with tailored public health campaigns.  

---

### **Day 3–4: Power BI Labs**  
- **Lab 1**: Import data into Power BI Desktop.  
- **Lab 2**: Transform/clean data using Power Query.  
- **Lab 7**: Design a report with visuals (e.g., charts, filters).  
- **Lab 10**: Create an interactive dashboard (technical issues noted).  
  - *Action*: Add screenshots once resolved.  

---

### **Key Takeaways**  
- **Tableau Public** is ideal for public-facing projects but lacks security/advanced features.  
- **Data Insights**:  
  - Music trends highlight demand for danceable, energetic tracks.  
  - Health data guides NHS in reducing disparities and improving preventative care.  
- **Power BI Skills**: Focus on data import, transformation, and dashboard creation for reporting.  


## ** Week 3 - SQL **

 **Short Summary of the Database Setup & Code:**

1. **Business Needs & Tables**  
   - **Goal**: Track inventory, sales, customers, and employees.  
   - **Tables Created**:  
     - `Products` (product details),  
     - `Customers` (loyalty program),  
     - `Sales` (transactions),  
     - `Employees` (staff access).  

2. **SQL Code for Tables**  
   - **Create Tables**:  
     ```sql  
     CREATE TABLE Products (  
       ProductID INT PRIMARY KEY AUTO_INCREMENT, -- Unique ID for each product  
       Name VARCHAR(255) NOT NULL,               -- Product name (e.g., "Milk")  
       StockQuantity INT NOT NULL,                -- Current stock (e.g., 100 units)  
       Price DECIMAL(5,2) NOT NULL                -- Price (e.g., £1.50)  
     );  
     ```  
   - **Sales Table Links to Customers/Products**:  
     ```sql  
     FOREIGN KEY (CustomerID) REFERENCES Customers(CustomerID),  
     FOREIGN KEY (ProductID) REFERENCES Products(ProductID)  
     ```  

3. **Automate Updates with Triggers**  
   - **After a Sale**:  
     ```sql  
     CREATE TRIGGER UpdateStockAfterSale  
     AFTER INSERT ON Sales  
     FOR EACH ROW  
     BEGIN  
       UPDATE Products  
       SET StockQuantity = StockQuantity - NEW.Quantity; -- Reduce stock when sold  
     END;  
     ```  
   - **Update Loyalty Points**:  
     ```sql  
     CREATE TRIGGER UpdateLoyaltyPoints  
     AFTER INSERT ON Sales  
     BEGIN  
       UPDATE Customers  
       SET LoyaltyPoints = LoyaltyPoints + NEW.TotalPrice; -- Add points based on purchase  
     END;  
     ```  

4. **Add Initial Data**  
   - Example for adding milk to the inventory:  
     ```sql  
     INSERT INTO Products (Name, StockQuantity, Price)  
     VALUES ('Milk', 100, 1.50);  
     ```  

5. **Maintenance & Security**  
   - **Backups**: Daily cloud/on-site backups.  
   - **Permissions**: Restrict staff to only view sales; managers can edit prices.  
   - **Data Quality**: Check for missing product details or duplicate customers.  

**Why It Works**:  
- **Efficiency**: Tables avoid duplicate data (e.g., products linked to sales via IDs).  
- **Accuracy**: Triggers auto-update stock and loyalty points.  
- **Security**: Role-based access protects sensitive data.  
    

### 📚 ** Week 5 workbook**

### **Day 1: Understanding Cloud Computing**
You learned what **cloud computing** is and how it's used in real life (like Netflix, Google Drive, or Microsoft 365). It helps businesses save money, stay flexible, work remotely, and keep data safe.

You also explored different types of **cloud models**:
- **Public Cloud** – shared services like AWS or Azure (great for startups).
- **Private Cloud** – exclusive to one organization (used by banks).
- **Hybrid Cloud** – mix of both (used by big companies like Toyota).
- **Community Cloud** – shared by similar organizations (like hospitals).

Then, you looked at **cloud services**:
- **IaaS** (Infrastructure as a Service) – basic building blocks (like virtual machines).
- **PaaS** (Platform as a Service) – tools for developers to build apps.
- **SaaS** (Software as a Service) – ready-to-use apps like Microsoft 365 or Zoom.

---

### **Day 2: Laws & Ethics in IT**
You studied **computer-related laws** like the:
- **Computer Misuse Act 1990** – illegal to access, modify, or damage computer systems without permission.
- **Police and Justice Act 2006** – expanded the law to include hackers and tools used for cybercrime.
- **Data Protection Act 2018 / GDPR** – ensures companies protect personal data like names, addresses, and health info.

You also discussed **ethical issues**, like avoiding plagiarism, not using pirated software, and knowing the risks (like viruses or legal fines).

---

### **Day 3: Exploring Azure Labs**
You worked on Microsoft Azure labs:
- **Relational Data** (like databases),
- **Non-Relational Data** (like document storage),
- **Data Analytics** (tools for analysing business data).  
One lab wasn’t working, so you plan to retry it.

---

### **Day 4: Team Practice & Case Study**

You worked on a **team practice exam** (DP-900), which helps prepare for Azure certifications.

Then you reviewed a business scenario for a company called **Paws & Whiskers**, a pet shop wanting to move from spreadsheets to Azure cloud for better efficiency.

---

## 🐾 **Paws & Whiskers Case Study Summary**

1. **Why They’re Moving to the Cloud:**
   - To better manage customer, sales, and stock data using tools like Azure SQL and Blob Storage.

2. **Legal Responsibilities:**
   - Must follow **GDPR** and **Data Protection Act** to keep customer data safe and private.
   - If handling payments, they must also follow **PCI DSS** standards.

3. **Recommended Azure Services:**
   - **Azure SQL Database** – for secure, structured data.
   - **Azure Blob Storage** – for receipts, images, etc.
   - **Azure Synapse & Machine Learning** – for analysing trends and customer behaviour.
   - **Azure Data Factory** – to automate data collection and integration.

4. **Types of Data & Modelling:**
   - Data includes customer info, product stock, sales transactions, and pet data.
   - Use **Relational Models** with IDs to link customers, sales, and inventory.
   - Data can be organised into a **data warehouse** for deeper analysis.

5. **Data Storage & Formats:**
   - Use **CSV** for raw imports, **JSON** for structured data, and **Parquet** for big data analytics.
   - Secure data with **encryption**, **role-based access**, and **MFA**.

6. **Other Important Considerations:**
   - Use **Azure Backup** and **Site Recovery** to avoid data loss.
   - Use **Power BI** for visual dashboards.
   - Azure can **scale** as the business grows.


---

### 📘 ** week 6 (Python & Data Practice)**

### **Day 2 – Python Challenge: FizzBuzz**
You tackled a popular coding interview question using Python:

- Go through numbers 1 to 100.
- If divisible by 3 → print **"fizz"**
- If divisible by 5 → print **"buzz"**
- If divisible by both 3 & 5 → print **"fizzbuzz"**
- Otherwise → print the number

✅ **Goal:** Practice writing `if`, `elif`, and `else` statements in Python.

---

### **Day 3 – Working with Student Data in Pandas**
You downloaded a file called `student.csv` and used **Pandas** to explore and analyze it.

#### 🔍 **Exercise 1: Loading and Exploring**
- Load the CSV into a **DataFrame**
- Show first 5 rows (`df.head()`)
- Get basic info (`df.info()`)
- Get summary stats like average, min, and max (`df.describe()`)

#### 🧾 **Exercise 2: Indexing and Slicing**
- Select columns like `name` or `mark`
- View first 3 rows
- Filter rows (e.g., students in class "Four")

#### 🛠 **Exercise 3: Data Manipulation**
- Add a `passed` column (True if mark ≥ 60)
- Rename `mark` to `score`
- Drop a column

#### 📊 **Exercise 4: Aggregation and Grouping**
- Group by `class` and get average marks
- Count students per class
- Compare averages by gender

#### 🔄 **Exercise 5: Advanced Operations**
- Create a **pivot table** to compare marks by class & gender
- Add a `grade` column (A, B, C, D based on score ranges)
- Sort students by score (high to low)

#### 💾 **Exercise 6: Exporting Data**
- Save your updated DataFrame (with grades) as a new CSV file

#### 📈 **Exercise 7: Visualisation (Bonus)**
- Optional: Try using charts or plots (like bar charts) to show your results using libraries like **Matplotlib** or **Seaborn**

---

### **Day 4 – Global Data Practice: GDP Data**

#### 🧮 **Task 1: Work with GDP Data**
You used a real-world dataset: **“GDP (nominal) per Capita.csv”**  
In Jupyter Notebook, you:
- Loaded the CSV file
- Printed the **first 10** and **last 5** rows
- Displayed only `Country/Territory` and `UN_Region` columns

#### 🧠 **Task 2: Fun with Data**
Using a shared Jupyter Notebook (`Day_4_Python_Activity.ipynb`), you:
- Explored and analyzed more GDP data
- Answered questions as a group
- Applied your skills creatively—no set rules, just practice and teamwork

---



