# Release Data Script

## Overview
The `release_data.py` script automates the process of fetching, filtering, and exporting GitHub pull request (PR) data for a specific repository. It retrieves PRs based on a given branch and date range, filters them by merge date, and then exports the relevant information (PR number, title, merge timestamp, team name, and release type) into a CSV file.

## Features
- Fetches pull requests from the `master` and `develop_uat` branches of a specified GitHub repository.
- Allows filtering of PRs by a custom date range.
- Identifies team names and release types based on branch and PR title.
- Exports the filtered PR data into a CSV file.
- Provides a loading animation for better user experience while fetching data.

## Prerequisites
- **Python 3.x** installed on your system.
- Necessary Python packages: `requests`, `json`, `datetime`, `os`, `csv`, `urllib3`.
- **GitHub Access Token** with repository read permissions.
- The repository's owner and name for which PR data needs to be fetched.

## How to Use

### 1. Install Required Libraries
Ensure you have the required libraries installed. You can install them using:

```bash
pip install requests
```

### 2. Configure GitHub Token and Repository Info

To use the GitHub API, you need to provide a personal access token and repository information. Follow these steps:

1. **Generate a GitHub Token:**
   - Go to your GitHub account's settings.
   - Navigate to **Developer settings** > **Personal access tokens**.
   - Click **Generate new token**, and select the necessary permissions (e.g., `repo` to read repository information).
   - Copy the generated token as you will need it later.

2. **Add Token and Repository Information to the Script:**
   Replace the following placeholders in the script with your GitHub token, repository owner, and repository name:

   ```python
   GITHUB_TOKEN = "<your-github-token>"
   REPO_OWNER = "<repo-owner>"
   REPO_NAME = "<repo-name>"
   ```
### 3. Run the Script

#### 3.1 Execute the Script
To run the script, use the following command in your terminal:

```bash
python release_data.py
```
#### 3.2 Input Date Range
When prompted, enter the start and end dates in the YYYY-MM-DD format. For example:

```bash
Enter the start date (YYYY-MM-DD): 2024-01-01
Enter the end date (YYYY-MM-DD): 2024-09-01
```
The script will then fetch the pull requests from the specified GitHub repository within the given date range.
As the script fetches data from GitHub, a loading animation will be displayed to indicate the progress of the data retrieval process.
After fetching and filtering the data, the script will generate a CSV file in the github folder, containing the details of the pull requests that were merged during the specified date range.


# PR Release Report Generator

This Python script generates a report on production releases from a CSV file containing merged pull request data. It processes the data to generate an Excel file and a PDF with visualizations and tables summarizing the production releases for each team.

## Features

- Reads pull request data from a CSV file.
- Normalizes team and branch names.
- Categorizes releases into "fast" and "slow" types.
- Outputs an Excel file with detailed release information for each team.
- Generates a PDF with the following:
  - A bar chart showing the number of production releases by team.
  - A pie chart comparing fast and slow releases.
  - A table summarizing total, fast, and slow releases by team.
  - Separate pages for each team with their release details and titles.

## Prerequisites

Make sure you have the following Python packages installed:

- `pandas`
- `matplotlib`
- `openpyxl`
- `collections` (built-in)
- `csv` (built-in)

You can install the required external packages using `pip`:

```bash
pip install pandas matplotlib openpyxl
```



### **Folder Structure**

```markdown
## Folder Structure

- **github**: The folder where the CSV file is stored.
- **reports**: The folder where the generated Excel and PDF files will be saved.

## Usage

1. Place the merged pull request CSV file in the `github` folder. The file should have the following columns:
    - `Team Name`
    - `Release Type`
    - `Branch`
    - `Title`

2. Update the `csv_file_name` variable in the script with the name of your CSV file (without the `.csv` extension).

3. Run the script:

```bash
python generate_graphs_prod.py
```

### **Example**

```markdown
### Example

```bash
python generate_graphs_prod.py
```
###**File Naming**

```markdown
## File Naming

- CSV file: `merged_prs_YYYY-MM-DD_to_YYYY-MM-DD.csv`
- Excel report: `pr_report.xlsx`
- PDF report: `pr_report_YYYY-MM-DD_to_YYYY-MM-DD.pdf`

```
## Output Format

- **Excel File**: Contains columns for team name, total releases, fast releases, slow releases, branches, and release titles. The "Releases" column will have line breaks for better readability.
  
- **PDF File**: Contains:
  - A bar chart showing the number of production releases by team.
  - A pie chart showing the proportion of fast and slow releases.
  - A table summarizing the release counts.
  - Detailed pages for each team with their production release titles.



