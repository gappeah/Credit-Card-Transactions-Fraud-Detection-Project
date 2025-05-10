# 🧾 Credit Card Transaction Dataset

## 📊 About the Dataset

This dataset contains **simulated credit card transactions** (both legitimate and fraudulent) spanning from **January 1, 2019** to **December 31, 2020** in the western United States. It includes information about each transaction including customer details, the merchant and category of purchase, and whether or not the transaction was a fraud.
The data was uploaded to [Kaggle](https://www.kaggle.com/datasets/kartik2112/fraud-detection) which was created using the [Sparkov Data Generation Tool](https://github.com/namebrandon/Sparkov_Data_Generation) by **Brandon Harris**.

It includes:

- Transactions from **1,000 customers**
- Across **800 merchants**
- Flagged with a `is_fraud` indicator

## Data Dictionary

| transdatetrans_time | Transaction DateTime                        |
|---------------------|---------------------------------------------|
| merchant            | Merchant Name                               |
| category            | Category of Merchant                        |
| amt                 | Amount of Transaction                       |
| city                | City of Credit Card Holder                  |
| state               | State of Credit Card Holder                 |
| lat                 | Latitude Location of Purchase               |
| long                | Longitude Location of Purchase              |
| city_pop            | Credit Card Holder's City Population        |
| job                 | Job of Credit Card Holder                   |
| dob                 | Date of Birth of Credit Card Holder         |
| trans_num           | Transaction Number                          |
| merch_lat           | Latitude Location of Merchant               |
| merch_long          | Longitude Location of Merchant              |
| is_fraud            | Whether Transaction is Fraud (1) or Not (0) |

## 🛠️ Source of Simulation

Sparkov uses:

- A Python library called `faker` to generate fake but realistic data
- Pre-defined customer profiles (e.g., "adults_2550_female_rural.json")
- Defined distributions for transaction frequency and amount

All profiles were merged to generate this unified dataset.

---

## 📁 Files Included

- `Credit_Card_DB.sql`: SQL dump of the full database
- `CreateTransactionTest.sql`: Script to manually create the `transactions_test` table
- `fraudTest.csv`: CSV export of the dataset for manual import [File was too large and therefore you need to download it separately from Kaggle]

---

## 🧱 Setting Up the Database in pgAdmin4

### 1. 🚀 Create a New Database

1. Open **pgAdmin4** and log into your PostgreSQL server.
2. Right-click on `Databases` → **Create** → **Database**.
3. Name it e.g., `credit_card_db` and click **Save**.

---

### 2. 📜 Restore SQL Dump (Optional)

If you'd like to directly restore the database:

1. Right-click the `credit_card_db` database → **Restore**
2. Format: `Custom or tar`
3. File: Navigate to `Credit_Card_DB.sql`
4. Click **Restore**

---

### 3. 🧱 OR: Run Table Creation Script

1. Select `credit_card_db`
2. Open the **Query Tool** (Tools → Query Tool)
3. Open `CreateTransactionTest.sql`
4. Run the script to create the `transactions_test` table

---

## 📥 Importing the CSV via pgAdmin4 
For a more detailed explanation please watch this [video](https://www.youtube.com/watch?v=UdMj8iKSCoc&list=LL&index=2) on have to load date from a CSV file to a PostgreSQL database in PgAdmin4
Once the table is created:

1. Right-click on the `transactions_test` table → **Import/Export**
2. **Filename**: Locate and select `fraudTest.csv`
3. Format: CSV
4. Encoding: `UTF8`
5. Delimiter: `,`
6. Header: ✅ (tick "Header")
7. Click **Import**

After import, run:

```sql
SELECT COUNT(*) FROM transactions_test;
```

to confirm successful insertion.

---

## 🧠 Use Cases

- Fraud Detection (ML/DL Models)
- Time-Series Analysis
- Behavioural Modeling
- Risk Scoring Systems

---


## 🙏 Acknowledgements

- **Brandon Harris** for building the Sparkov simulation engine
- Credit to the open-source community for supporting realistic data simulations for public use

---
