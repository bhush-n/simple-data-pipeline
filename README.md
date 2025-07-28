# simple-data-pipeline

Simple Data Pipeline with Python and Docker
A straightforward ETL (Extract, Transform, Load) data pipeline implementation using Python and Docker for processing medical datasets.

Overview
This project demonstrates how to build a simple yet effective data pipeline that extracts data from a CSV file, transforms it by cleaning and standardizing the format, and loads the processed data into a new file. The entire pipeline runs in a Docker container for consistent execution across different environments.

Features
Extract: Read data from CSV files

Transform: Clean data by removing missing values and standardizing column names

Load: Save processed data to a new CSV file

Containerized: Runs in Docker for environment consistency

Simple Setup: Minimal configuration required

Project Structure
text
simple-data-pipeline/
├── app/
│   └── pipeline.py          # Main pipeline script
├── data/
│   ├── Medicaldataset.csv   # Source dataset
│   └── CleanedMedicalData.csv # Output (generated)
├── Dockerfile               # Docker configuration
├── requirements.txt         # Python dependencies
├── docker-compose.yml       # Docker Compose configuration
└── README.md               # This file
Prerequisites
Docker and Docker Compose installed on your system

Basic understanding of Python and Docker concepts

Setup and Installation
Clone or download the project files to your local machine

Ensure the project structure matches the layout shown above

Verify the dataset is placed in the data/ folder as Medicaldataset.csv

Usage
Running the Pipeline
Execute the following command from the project root directory:

bash
docker compose up --build
Expected Output
When the pipeline runs successfully, you should see output similar to:

text
✔ data-pipeline                           Built                                                                                   0.0s 
✔ Network simple_docker_pipeline_default  Created                                                                                 0.4s 
✔ Container simple_pipeline_container     Created                                                                                 0.4s 
Attaching to simple_pipeline_container
simple_pipeline_container  | Data Extraction completed.
simple_pipeline_container  | Data Transformation completed.
simple_pipeline_container  | Data Loading completed.
simple_pipeline_container  | Data pipeline completed successfully.
simple_pipeline_container exited with code 0
Results
After successful execution, you'll find a new file CleanedMedicalData.csv in the data/ folder containing the processed dataset.

Pipeline Components
Extract Phase
Reads the source CSV file from the mounted data directory

Uses pandas to load the dataset into memory

Transform Phase
Removes rows with missing values using dropna()

Standardizes column names by:

Converting to lowercase

Replacing spaces with underscores

Trimming whitespace

Load Phase
Saves the cleaned dataset to a new CSV file

Maintains data integrity without index columns

Dataset Information
The pipeline processes a medical dataset (Medicaldataset.csv) containing the following features:

Age, Gender, Heart rate

Blood pressure measurements (Systolic/Diastolic)

Blood sugar levels

Cardiac markers (CK-MB, Troponin)

Result classification (positive/negative)

The cleaned output (CleanedMedicalData.csv) contains the same data with standardized column names and removed missing values.

Docker Configuration
Dockerfile
Based on Python 3.10 slim image

Installs required dependencies from requirements.txt

Sets up the working environment in /app

Docker Compose
Builds the container from the current directory

Mounts the local data/ folder to /data in the container

Provides easy execution with a single command

Dependencies
The project uses minimal dependencies listed in requirements.txt:

pandas: For data manipulation and CSV operations

Customization
To adapt this pipeline for your own data:

Replace the dataset: Place your CSV file in the data/ folder

Modify the pipeline: Update pipeline.py to handle your specific data transformation needs

Adjust paths: Update the input_path and output_path variables in the script

Add dependencies: Include any additional libraries in requirements.txt

Troubleshooting
Common Issues
File not found: Ensure your dataset is in the data/ folder with the correct filename

Permission errors: Check that Docker has access to your project directory

Build failures: Verify that requirements.txt contains valid package names

Debugging
To debug issues, you can run the container interactively:

bash
docker run -it --rm -v ./data:/data simple-data-pipeline bash
Future Enhancements
This basic pipeline can be extended with:

Database connectivity for data sources and destinations

Data validation and quality checks

Error handling and logging

Configuration files for different environments

Scheduling and automation capabilities

Monitoring and alerting features

Contributing
Feel free to fork this project and submit improvements. Some areas for contribution:

Enhanced error handling

Support for different data formats

More sophisticated data transformations

Integration with data warehouses

License
This project is provided as-is for educational and demonstration purposes.

Acknowledgments
Based on the tutorial by Cornellius Yudha Wijaya, demonstrating practical data pipeline implementation with modern tools.
