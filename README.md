# 🔎 Data Engineer Job Scraper

A Python web scraping project that uses **Selenium** to collect real-time **Data Engineer job listings** from [Naukrigulf](https://www.naukrigulf.com/), organize the extracted information using **Pandas**, and export the results into a structured CSV file.

The project demonstrates practical skills in **web automation, web scraping, data extraction, data structuring, and CSV data storage**.

---

## 📌 Project Overview

Finding and analyzing job opportunities manually can be time-consuming. This project automates the process of collecting Data Engineer job listings from a live job portal.

The scraper:

* Opens Naukrigulf using Selenium.
* Searches for **"Data Engineer"** positions.
* Navigates through multiple pages of search results.
* Extracts important information from each job listing.
* Stores the collected data in a Python list of dictionaries.
* Converts the data into a Pandas DataFrame.
* Exports the final dataset to a CSV file.

### 🎯 Objective

> *Use Selenium with Python to scrape real job listings from a live job portal and store the extracted information in a structured CSV dataset.*

---

## 🛠️ Technologies & Libraries

| Technology           | Purpose                                     |
| -------------------- | ------------------------------------------- |
| **Python**           | Main programming language                   |
| **Selenium**         | Browser automation and web scraping         |
| **Pandas**           | Data organization and DataFrame creation    |
| **Chrome WebDriver** | Automates Google Chrome                     |
| **CSV**              | Stores the final structured dataset         |
| **Jupyter Notebook** | Development and experimentation environment |

### Python Libraries

```python
selenium
pandas
time
```

---

## 🔄 Project Workflow

```text
                 ┌─────────────────────┐
                 │     Naukrigulf      │
                 │    Job Portal       │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │      Selenium       │
                 │  Browser Automation │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Search "Data        │
                 │ Engineer" Jobs      │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Extract Job Details │
                 └──────────┬──────────┘
                            │
              ┌─────────────┼─────────────┐
              ▼             ▼             ▼
          Job Title      Company       Location
              │             │             │
              └─────────────┼─────────────┘
                            │
                            ▼
                    Experience
                            │
                            ▼
                       Description
                            │
                            ▼
                 ┌─────────────────────┐
                 │   Python List of    │
                 │     Dictionaries    │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │      Pandas         │
                 │    DataFrame        │
                 └──────────┬──────────┘
                            │
                            ▼
                 ┌─────────────────────┐
                 │ Data_Engineer_      │
                 │ jobs.csv            │
                 └─────────────────────┘
```

---

## 📊 Data Collected

For each job listing, the scraper extracts the following fields:

| Field          | Description                      |
| -------------- | -------------------------------- |
| `job_title`    | Title of the advertised position |
| `company_name` | Company offering the position    |
| `job_location` | Job location                     |
| `experience`   | Required experience              |
| `description`  | Job description                  |

Example structure:

```python
{
    "job_title": "Data Engineer",
    "company_name": "Example Company",
    "job_location": "Dubai - United Arab Emirates",
    "experience": "3 - 5 Years",
    "description": "Design ETL pipelines and manage data..."
}
```

---

## ⚙️ How It Works

### 1. Configure Selenium

Chrome WebDriver is configured with several browser options before launching the browser.

```python
from selenium import webdriver
from selenium.webdriver.chrome.options import Options

options = Options()

options.add_argument("--window-size=1500,950")
options.add_argument("--disable-gpu")
options.add_argument("--no-sandbox")
options.add_argument("--disable-dev-shm-usage")

driver = webdriver.Chrome(options=options)
```

---

### 2. Search for Data Engineer Jobs

The scraper opens Naukrigulf and performs a job search for:

```text
Data Engineer
```

Selenium interacts with the search interface automatically.

---

### 3. Extract Job Information

The scraper locates job cards using Selenium selectors and extracts:

```python
job_title
company_name
job_location
experience
description
```

The information is then stored in a list:

```python
list_jobs.append({
    'job_title': job_title,
    'company_name': company_name,
    'job_location': job_location,
    'experience': experience,
    'description': description
})
```

---

### 4. Navigate Through Multiple Pages

The scraper processes **three pages** of job listings.

After processing each page, Selenium clicks the navigation control and continues to the next page.

```python
for i in range(3):
    ...
```

---

### 5. Convert Data Into a DataFrame

Once the scraping process is complete, the collected records are converted into a Pandas DataFrame:

```python
import pandas as pd

df = pd.DataFrame(list_jobs)
```

This creates a structured tabular dataset that can easily be analyzed or exported.

---

### 6. Export the Dataset

Finally, the DataFrame is saved as:

```text
Data_Engineer_jobs.csv
```

using:

```python
df.to_csv('Data_Engineer_jobs.csv')
```

---

## 📁 Project Structure

```text
Data-Engineer-Job-Scraper/
│
├── 📓 Selenium_Project.ipynb
│
├── 📄 Data_Engineer_jobs.csv
│
└── 📄 README.md
```

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

* Python 3.x
* Google Chrome
* ChromeDriver / Selenium Manager
* Jupyter Notebook or JupyterLab

### Install Dependencies

Clone the repository:

```bash
git clone https://github.com/your-username/Data-Engineer-Job-Scraper.git
```

Navigate to the project directory:

```bash
cd Data-Engineer-Job-Scraper
```

Install the required Python packages:

```bash
pip install selenium pandas
```

---

## ▶️ Running the Project

Open the Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Selenium_Project.ipynb
```

Run the notebook cells sequentially.

The scraper will open Chrome, search for Data Engineer positions, collect the job information, create a DataFrame, and generate:

```text
Data_Engineer_jobs.csv
```

---

## 📈 Possible Extensions

This project can be extended into a more advanced job-market data pipeline.

Potential improvements include:

* 🔹 Scrape more than three pages.
* 🔹 Collect job posting URLs.
* 🔹 Extract salary information when available.
* 🔹 Extract required technical skills.
* 🔹 Add job posting dates.
* 🔹 Remove duplicate job listings.
* 🔹 Handle pagination automatically.
* 🔹 Add stronger exception handling.
* 🔹 Store data directly in a SQL database.
* 🔹 Schedule the scraper to run automatically.
* 🔹 Build a Power BI dashboard for job-market analysis.
* 🔹 Analyze the most requested Data Engineering skills.
* 🔹 Analyze job distribution by country and company.
* 🔹 Build a complete ETL pipeline from scraping → cleaning → database → visualization.

---

## 🧠 Skills Demonstrated

This project demonstrates practical experience with:

**Python**

* Lists
* Dictionaries
* Loops
* Exception handling
* File export

**Web Scraping**

* Selenium WebDriver
* DOM element selection
* XPath
* CSS/class-based selectors
* Browser automation
* Pagination

**Data Engineering**

* Data extraction
* Data structuring
* Data transformation
* CSV data storage
* Pandas DataFrames

**Automation**

* Automated browser interaction
* Automated job searching
* Automated multi-page data collection

---

## ⚠️ Notes

This project was created for **educational and data-engineering practice purposes**.

Websites can change their HTML structure, class names, navigation elements, or access policies. As a result, Selenium selectors may need to be updated if the target website changes.

The scraper should also be used responsibly and in accordance with the target website's terms of service and applicable policies.

---

## 👨‍💻 Author

**Kareem Emara**

Computer & Communications Engineering | Data Engineering & Analytics

Currently developing skills in **Microsoft Data Engineering**, with a focus on Python, SQL, data processing, and data engineering practices.

### Connect With Me

* 🌐 **Portfolio:** [Kareem Emara — Data Engineering & Analytics Portfolio](https://kareememara99.github.io/portfolio/)
* 💼 **LinkedIn:** [Kareem Emara](https://linkedin.com/in/kareem-emara-83b81a303)
* 🐙 **GitHub:** [Kareem Emara](https://github.com/Kareememara99)

---

## ⭐ If You Found This Project Useful

Feel free to **star ⭐ the repository** and explore the other projects in my portfolio.

> **Turning Data Into Business Value.**
