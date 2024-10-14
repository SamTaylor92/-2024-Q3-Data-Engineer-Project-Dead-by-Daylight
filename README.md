![Sam Taylor](https://user-images.githubusercontent.com/105542266/168467543-3057e37f-781f-445d-b953-88624c438755.png)

<p align="right"> <a 
href="https://stackoverflow.com/users/18680621/sam-taylor" target="_blank"><img alt="StackOverflow" 
src="https://stackoverflow-badge.vercel.app/?userID=18680621" /></a> <a 
href="https://github.com/SamTaylor92" target="_blank"><img alt="Github" 
src="https://img.shields.io/badge/GitHub-181717.svg?style=for-the-badge&logo=GitHub&logoColor=white" /></a> <a 
href="https://www.linkedin.com/in/samjamest" target="_blank"><img alt="LinkedIn" 
src="https://img.shields.io/badge/LinkedIn-0A66C2.svg?style=for-the-badge&logo=LinkedIn&logoColor=white" /></a> <a 
href="https://signal.group/#CjQKIO50NLkjJmSisbgDD4OhRj5lHG7X-SJTOl-Dn8Fkc4FpEhCYdnCVL1ok4DlVNntY3mGe" target="_blank"><img alt="Signal" src="https://img.shields.io/badge/Signal-3A76F0.svg?style=for-the-badge&logo=Signal&logoColor=white"/></a> <a 
href="mailto:samtaylor92@live.co.uk" target="_blank"><img alt="Email" src="https://img.shields.io/badge/Gmail-D14836?style=for-the-badge&logo=gmail&logoColor=white" /></a>
</p>
<p align="right">
  
# [2024 Q3] Data Engineer Project: Dead by Daylight ETL Pipeline

## Overview

This project focuses on building an **ETL pipeline** for **Dead by Daylight** game data. The pipeline processes data from various game entities such as characters, perks, maps, addons, and match details. Using **Databricks** and **Apache Spark**, we designed the pipeline to transform, clean, and load data into structured formats that support game balancing analysis, player performance tracking, and game element ratings.

The data is sourced from [Dennis Reep's Dead by Daylight website](https://dennisreep.nl/dbd/), and integrated into a database designed to store, manage, and analyze key elements for decision-making around the game.

<div align="center">
    <img src="https://github.com/user-attachments/assets/102c63d3-70e5-46b7-b318-33c8b0b3601b" alt="dbd">
</div>

## Table of Contents

- [Technologies Used](#technologies-used)
- [Pipeline Architecture](#pipeline-architecture)
- [Project Structure](#project-structure)
- [Data Sources](#data-sources)
- [Installation & Setup](#installation--setup)
  - [Prerequisites](#prerequisites)
  - [Setup](#setup)
- [Usage](#usage)
- [Contributing](#contributing)
- [License](#license)

## Technologies Used

- **Apache Spark** (Databricks)
- **Python**
- **Delta Lake**
- **Amazon S3** for storage
- **Git** for version control

## Pipeline Architecture

1. **Extract**:
   - Data is scraped monthly from the [Dennis Reep Dead by Daylight Website](https://dennisreep.nl/dbd/).
   - Data includes ratings, tier lists for killers and survivors, perks, and map biases.

2. **Transform**:
   - Data cleaning includes renaming columns, handling nulls, and transforming data types.
   - Special care is given to **perk ratings**, **character costs**, and **match outcomes**.
   - Additions of new columns like `total_cost_euros` and `is_licensed` for characters.

3. **Load**:
   - Processed data is loaded into **Delta Lake**, using staging (`stg_`), dimension (`dim_`), and fact (`fact_`) tables.
   - Fact tables contain aggregated match statistics, killer and survivor perks, and map ratings.

## Project Structure

```bash
dbd/
├── dbd.ipynb                                                       # Notebook for running the ETL, transform and analysis process
├── img/                                                            # Contains any images used in the final presentation
├── resources/                                                      # Contains Conceptual and Logical database models for the database created
├── [August 2024] Dead by Daylight_ Database documentation.pdf      # Documentation for the project
├── [August 2024] Dead by Daylight.pdf                              # Presentation for the project 
├── README.md                                                       # Github documentation (this file)
└── requirements.txt                                                # Python dependencies for the project
```
## Data Sources

Data is scraped from:

- [Dennis Reep Dead by Daylight Database](https://dennisreep.nl/dbd/): Contains game ratings, perk tier lists, and map biases.
- Google Sheets for custom match data.

## Installation & Setup

### Prerequisites
- Python 3.7+ is required.
- Install dependencies via `pip` or `conda` using the provided `requirements.txt` file.

### Setup
1. Clone the repository:
```bash
git clone https://github.com/SamTaylor92/2024-Q3-Data-Engineer-Project-Dead-by-Daylight.git
cd dbd
```

2. Install dependencies:
```bash
pip install -r requirements.txt
```

3. Configure your environment with the necessary connections using the `requirements.txt` file.

4. Load the notebook from the directory to your workspace.

## Usage

1. Run ETL:
- Start the ingestion by running the notebook
- Transformation processes clean, normalize, and add features like DLC costs and ratings.

2. Transform Data:
- The data is not currently containerised, so one run of the data will also complete the ETL, transform and analysis steps.
  
3. Analyze:
- The data is not currently containerised, so one run of the data will also complete the ETL, transform and analysis steps.

## Contributing

Contributions are welcome! Please follow these steps:

- Fork the repository.
- Create a feature branch (`git checkout -b feature-name`).
- Commit your changes (`git commit -m 'Add feature'`).
- Push to your branch (`git push origin feature-name`).
- Create a pull request.

## License

This project is licensed under the MIT License.
