# AI-ML-Jobs-Intelligence-Report-for-MENA-Region-streamlit-

---

A multi-agent system designed to analyze job trends for AI and Machine Learning roles in the MENA region and generate a customized PDF report. The system collects job data, extracts structured information, analyzes trends, and produces a professional report with visualizations, all through an interactive **Streamlit** web interface.

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Project Structure](#project-structure)
- [Requirements](#requirements)
- [Setup Instructions](#setup-instructions)
- [Usage](#usage)
- [Extending the System](#extending-the-system)
- [Troubleshooting](#troubleshooting)
- [License](#license)

## Project Overview
This project implements a multi-agent system to:
1. Collect job listings for AI/ML roles in the MENA region (currently simulated with mock data).
2. Extract structured data (job titles, skills, and locations).
3. Analyze trends to identify the top 10 job titles, required skills, and geographic distribution.
4. Generate a professional PDF report with tables and visualizations.

The system uses **Streamlit** to provide a user-friendly web interface for selecting countries, specifying a time period, and downloading the generated report.

## Features
- **Multi-Agent Architecture**:
  - `WebSearchAgent`: Simulates fetching job listings (extendable for real scraping).
  - `DataExtractionAgent`: Extracts job titles, skills, and countries.
  - `TrendAnalysisAgent`: Analyzes data to identify trends and generate visualizations.
  - `ReportWriterAgent`: Creates a PDF report with tables and charts.
- **Streamlit Interface**: Interactive web UI to:
  - Select countries and time period.
  - Display progress notifications.
  - Download the generated PDF report.
- **Visualizations**: Bar charts for top jobs, skills, and geographic distribution.
- **Output**: Professional PDF report saved in the `reports` directory.

## Project Structure
```
├── main.py                        # Main script with Streamlit interface
├── agents/
│   ├── web_search_agent.py       # Agent for collecting job listings
│   ├── data_extraction_agent.py  # Agent for extracting structured data
│   ├── trend_analysis_agent.py   # Agent for analyzing trends and generating plots
│   └── report_writer_agent.py    # Agent for generating PDF report
├── reports/
│   └── MENA_AI_Jobs_Report.pdf   # Generated PDF report
├── requirements.txt              # Required Python libraries
├── README.md                     # Project documentation
```

## Requirements
- Python 3.8 or higher
- Libraries listed in `requirements.txt`:
  ```
  streamlit==1.31.0
  pandas==2.2.2
  requests==2.32.3
  beautifulsoup4==4.12.3
  matplotlib==3.9.2
  seaborn==0.13.2
  reportlab==4.2.2
  numpy==2.0.2
  ```

## Setup Instructions
1. **Clone or Download the Project**:
   Download the project files to a directory, e.g., `C:\Users\YourName\ai-ml-jobs-mena`.

2. **Set Up a Python Environment** (optional but recommended):
   ```bash
   python -m venv venv
   source venv/bin/activate  # On Windows: venv\Scripts\activate
   ```

3. **Install Dependencies**:
   Navigate to the project directory and install the required libraries:
   ```bash
   pip install -r requirements.txt
   ```

4. **Create the `reports` Directory** (optional):
   The system automatically creates the `reports` directory, but you can create it manually if needed:
   ```bash
   mkdir reports
   ```

## Usage
Run the Streamlit application to launch the web interface, where you can configure the analysis and download the report.

### Run the Application
```bash
streamlit run main.py
```

This opens a web browser with the Streamlit interface. Follow these steps:
1. **Select Countries**: Choose one or more MENA countries (e.g., Egypt, Saudi Arabia, UAE) from the dropdown.
2. **Select Time Period**: Use the slider to specify the analysis period (1-12 months).
3. **Start Analysis**: Click the "Start Analysis" button to run the pipeline.
4. **Download Report**: Once generated, a download button appears for the `MENA_AI_Jobs_Report.pdf`.

### Optional CLI Mode
For automated execution without the UI, run:
```bash
python main.py --cli
```
This uses default settings (countries: Egypt, Saudi Arabia, UAE; time period: 6 months).

### Example Output
In the Streamlit interface, you’ll see progress messages like:
```
Fetching job listings...
Extracting job details...
Analyzing job trends...
Generating PDF report...
```
The generated PDF report (`MENA_AI_Jobs_Report.pdf`) is saved in the `reports` directory and includes:
- Top 10 AI/ML job titles with counts.
- Top required skills with frequencies.
- Geographic distribution of jobs by country.
- Visualizations (bar charts) for each analysis.

## Extending the System
- **Real Web Scraping**: Replace mock data in `web_search_agent.py` with actual scraping using `BeautifulSoup` or `Selenium` for platforms like LinkedIn, Bayt, or Wuzzuf. Handle authentication and rate limits as needed.
- **Database Integration**: Store job listings in a database (e.g., SQLite) for scalability.
- **Additional Analysis**: Add agents for sentiment analysis, salary trends, or real-time data updates.
- **Custom Visualizations**: Enhance charts using libraries like Plotly for interactive visuals.

## Troubleshooting
- **ModuleNotFoundError**:
  Ensure all dependencies are installed:
  ```bash
  pip install -r requirements.txt
  ```
  Verify the Python environment:
  ```bash
  python --version
  pip list
  ```
- **FileNotFoundError**:
  If errors occur when saving plots or the PDF (e.g., `reports/top_jobs.png`), the system now automatically creates the `reports` directory. If issues persist, manually create it:
  ```bash
  mkdir reports
  ```
- **Plotting Issues**:
  If visualizations fail, ensure Matplotlib uses the `Agg` backend. Add to `trend_analysis_agent.py`:
  ```python
  import matplotlib
  matplotlib.use('Agg')
  ```
- **Permissions**: Run the command prompt as an administrator if you encounter permission errors in the project directory.
- **Streamlit Issues**: Ensure the correct Python environment is active. If the browser doesn’t open, access the app at `http://localhost:8501`.

## License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details (if applicable).

---

### Notes
- This `README.md` is tailored for the Streamlit-based version, reflecting the interactive web interface.
- The implementation includes the fix for the previous `FileNotFoundError` by ensuring the `reports` directory is created in `trend_analysis_agent.py`.
- The Streamlit interface provides a user-friendly experience with progress notifications and a download button for the PDF report.
- For real-world use, extend `WebSearchAgent` to integrate actual web scraping, as the current implementation uses mock data.

