# i202656-MLOPs-Assignment-2
Name: Muneeba Aftab 

Contact: i202656@nu.edu.pk  

MLOps Implementation with Apache Airflow (Implementation of Apache Airflow to automate data extraction, transformation, and version-controlled storage).

### Data Extraction
- Got articles from BBC and Dawn using a tool called BeautifulSoup along with requests. Then, I only kept the important links and removed the ones I didn't need.

### Data Transformation
- Cleaned up the articles, getting rid of any messy HTML code, extra spaces, and making sure all the text looked the same.

### Data Loading
- Saved processed articles to a JSON file, which makes it easy for us to use the data later on.

# DVC Setup
1. Install DVC:
    ```bash
    pip install dvc
    ```
2. Initialize DVC setup in your repository:
    ```bash
    dvc init
    ```
3. Add remote storage (e.g., Google Drive), connected DVC to a place where we can save our files:
    ```bash
    dvc remote add -d gdrive_remote gdrive://your_folder_id
    ```
4. Keeping Track of data files with DVC:
    ```bash
    dvc add data/articles.json
    ```
5. Push data to the remote:
    ```bash
    dvc push
    ```

## Workflow and Challenges

### Workflow
1. **Airflow DAG:** 
    - Implemented an ETL pipeline using Airflow to manage data extraction, transformation, and loading.

2. **DVC Integration:**
    - Used DVC to keep track of our data, for data version control and reproducibility.
    - Setup Google Drive as remote storage.

### Challenges
- **Data Access Issues:** 
  - Sometimes, the websites I tried to get data from didn't have the same structure, so it was hard to grab the information we needed. We made sure our plan could handle these problems.
  - Implemented error handling and retries.

- **Environment Setup:**
  - It was tricky to get Airflow to work properly on Windows. I solved this by using a special tool called WSL2, which makes Windows act like a different type of computer that works better with Airflow (POSIX-compliant environment).


## MLOps Project: ETL with Airflow and DVC

### Overview
- I made a special process to get data, clean it up, and store it. We used Airflow to manage this process and DVC to keep track of our data.

### Setup Instructions
Step 1. Clone the repository and install dependencies:
    ```bash
    git clone https://github.com/muneeba-aftab/i202656-MLOPs-Assignment-2.git
    cd i202656-MLOPs-Assignment-2
    pip install -r requirements.txt
    ```

Step 2. InitializING Airflow:
    ```bash
    airflow db init
    ```

Step 3. Run the web server and scheduler:
    ```bash
    airflow webserver -p 8080
    airflow scheduler
    ```

### Usage
- You can start the process using Airflow's special website. Just click on the name of our plan, mlops_etl_dag, and choose "run" to start the process.



