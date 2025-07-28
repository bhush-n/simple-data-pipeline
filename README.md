# Simple Data Pipeline with Python and Docker

A straightforward ETL (Extract, Transform, Load) data pipeline implementation using **Python** and **Docker** for processing medical datasets.

---

## 📌 Overview
This project demonstrates how to build a simple yet effective data pipeline that:
- **Extracts** data from a CSV file.
- **Transforms** it by cleaning and standardizing the format.
- **Loads** the processed data into a new file.

The entire pipeline runs in a Docker container for consistent execution across different environments.

---

## ✨ Features
- ✅ **Extract**: Read data from CSV files  
- ✅ **Transform**: Clean data by removing missing values and standardizing column names  
- ✅ **Load**: Save processed data to a new CSV file  
- ✅ **Containerized**: Runs in Docker for environment consistency  
- ✅ **Simple Setup**: Minimal configuration required  

---

## 📂 Project Structure
```
simple-data-pipeline/
├── app/
│   └── pipeline.py             # Main pipeline script
├── data/
│   ├── Medicaldataset.csv      # Source dataset
│   └── CleanedMedicalData.csv  # Output (generated)
├── Dockerfile                  # Docker configuration
├── requirements.txt            # Python dependencies
├── docker-compose.yml          # Docker Compose configuration
└── README.md                   # Project documentation
```

---

## 🛠️ Prerequisites
- Docker and Docker Compose installed on your system  
- Basic understanding of Python and Docker concepts  

---

## 🚀 Setup and Installation
1. **Clone or download** the project files to your local machine  
2. Ensure the project structure matches the layout shown above  
3. Place your dataset in the `data/` folder as `Medicaldataset.csv`

---

## ▶️ Usage

### Running the Pipeline
From the project root directory, execute:

\`\`\`bash
docker compose up --build
\`\`\`

---

## ✅ Expected Output
After running, you should see logs similar to:


✔ data-pipeline                           Built
✔ Network simple_docker_pipeline_default  Created
✔ Container simple_pipeline_container     Created
Attaching to simple_pipeline_container
simple_pipeline_container  | Data Extraction completed.
simple_pipeline_container  | Data Transformation completed.
simple_pipeline_container  | Data Loading completed.
simple_pipeline_container  | Data pipeline completed successfully.
simple_pipeline_container exited with code 0


The cleaned dataset will be available in the `data/` folder as **`CleanedMedicalData.csv`**.

---

## 🔍 Pipeline Components

### 1. **Extract Phase**
- Reads the source CSV file from the mounted `data/` directory  
- Uses **pandas** to load the dataset into memory  

### 2. **Transform Phase**
- Removes rows with missing values using `dropna()`  
- Standardizes column names by:
  - Converting to lowercase  
  - Replacing spaces with underscores  
  - Trimming whitespace  

### 3. **Load Phase**
- Saves the cleaned dataset to a new CSV file  
- Maintains data integrity without index columns  

---

## 📊 Dataset Information
The pipeline processes a medical dataset (`Medicaldataset.csv`) with features like:
- Age, Gender, Heart rate  
- Blood pressure measurements (Systolic/Diastolic)  
- Blood sugar levels  
- Cardiac markers (CK-MB, Troponin)  
- Result classification (positive/negative)  

The cleaned output (`CleanedMedicalData.csv`) contains standardized column names and no missing values.

---

## 🐳 Docker Configuration

### **Dockerfile**
- Based on `python:3.10-slim`  
- Installs dependencies from `requirements.txt`  
- Sets up the working directory `/app`

### **Docker Compose**
- Builds the container from the current directory  
- Mounts local `data/` folder to `/data` in the container  
- Allows easy execution with a single command  

---

## 📦 Dependencies
The project uses:
\`\`\`
pandas
\`\`\`
(defined in `requirements.txt`)

---

## ⚡ Customization
- Replace the dataset in `data/` with your own CSV file  
- Modify `pipeline.py` to handle custom transformations  
- Update paths as required (`input_path` & `output_path`)  
- Add more dependencies in `requirements.txt` if needed  

---

## 🛠️ Troubleshooting

| Issue | Solution |
|--------|-----------|
| **File not found** | Ensure the dataset is in `data/` with the correct filename |
| **Permission errors** | Check Docker access to your project directory |
| **Build failures** | Verify `requirements.txt` contains valid package names |

### Debugging
Run the container interactively for debugging:
\`\`\`bash
docker run -it --rm -v ./data:/data simple-data-pipeline bash
\`\`\`

---

## 🚀 Future Enhancements
- Database connectivity for data sources/destinations  
- Data validation and quality checks  
- Error handling and logging  
- Configuration files for multiple environments  
- Scheduling and automation  
- Monitoring and alerting  

---

## 🤝 Contributing
Contributions are welcome!  
Some areas for improvement:
- Enhanced error handling  
- Support for multiple data formats  
- Advanced transformation logic  
- Integration with data warehouses  

---

## 📜 License
This project is provided **as-is** for educational and demonstration purposes.

---

## 🙌 Acknowledgments
Inspired by the tutorial by **Cornellius Yudha Wijaya**, demonstrating practical data pipeline implementation with modern tools.
