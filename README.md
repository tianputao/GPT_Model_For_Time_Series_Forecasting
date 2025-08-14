# Data Predictive Analysis by GPT Time series model

This project performs time series analysis and forecasting on transaction data using TimeGPT and pandas for data processing.

## 📋 Table of Contents

- [Project Overview](#project-overview)
- [Prerequisites](#prerequisites)
- [Installation](#installation)
- [VS Code Setup](#vs-code-setup)
- [Data Structure](#data-structure)
- [Usage Instructions](#usage-instructions)
- [File Descriptions](#file-descriptions)
- [Troubleshooting](#troubleshooting)

## 🎯 Project Overview

This project analyzes transaction data to:
- Merge and clean transaction data from multiple sources
- Transform timestamps to standardized format
- Aggregate data to minute-level time series
- Perform time series forecasting using TimeGPT
- Generate confidence intervals for predictions

## 🔧 Prerequisites

- Python 3.8 or higher
- VS Code (Visual Studio Code)
- Internet connection for TimeGPT API

## 📦 Installation

### Step 1: Clone or Download the Project

```bash
git clone https://github.com/tianputao/GPT_Model_For_Time_Series_Forecasting.git
cd GPT_Model_For_Time_Series_Forecasting
```

### Step 2: Install Python Dependencies

#### Option A: Using pip

```bash
# Upgrade pip first
python -m pip install --upgrade pip

# Install from requirements file
pip install -r requirements.txt
```

#### Option B: Manual Installation

```bash
# Install packages individually
pip install pandas>=2.0.0
pip install numpy>=1.24.0
pip install nixtla>=0.5.0
pip install zstandard>=0.21.0
```

### Step 3: Verify Installation

Run the following Python script to verify all packages are installed correctly:

```python
import sys
print(f"Python version: {sys.version}")

try:
    import pandas as pd
    print(f"✓ pandas version: {pd.__version__}")
except ImportError:
    print("✗ pandas not installed")

try:
    import numpy as np
    print(f"✓ numpy version: {np.__version__}")
except ImportError:
    print("✗ numpy not installed")

try:
    from nixtla import NixtlaClient
    print("✓ nixtla installed successfully")
except ImportError:
    print("✗ nixtla not installed")

try:
    import zstandard
    print("✓ zstandard installed successfully")
except ImportError:
    print("✗ zstandard not installed")
```

## 🖥️ VS Code Setup

### Install VS Code

1. Download and install VS Code from [https://code.visualstudio.com/](https://code.visualstudio.com/)

### Install Jupyter Extension

1. Open VS Code
2. Go to Extensions (Ctrl+Shift+X or Cmd+Shift+X on Mac)
3. Search for "Jupyter"
4. Install the official "Jupyter" extension by Microsoft
5. Also install "Python" extension by Microsoft

### Setup Python Environment

1. Open VS Code
2. Open the project folder: `File > Open Folder` → Select `GPT_Model_For_Time_Series_Forecasting`
3. Press `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac) to open Command Palette
4. Type "Python: Select Interpreter"
5. Choose the Python interpreter where you installed the packages

### Working with Jupyter Notebooks

#### Opening a Notebook

1. In VS Code, navigate to the `src/` folder
2. Click on any `.ipynb` file (e.g., `data_transform.ipynb` or `forecast.ipynb`)
3. The notebook will open in VS Code

#### Selecting Kernel

1. With a notebook open, look at the top-right corner of the VS Code window
2. Click on the kernel selector (it might show "Python 3.x.x" or "Select Kernel")
3. Choose "Python Environments..."
4. Select the Python interpreter where you installed the packages

#### Running Cells

- **Run single cell**: Click the play button (▶️) next to a cell or press `Shift+Enter`
- **Run all cells**: Press `Ctrl+F5` or use Command Palette → "Jupyter: Run All Cells"
- **Run cell and advance**: Press `Shift+Enter`


## 🚀 Usage Instructions

### Step 1: Data Transformation

1. Open `src/data_transform.ipynb` in VS Code
2. Ensure your input data files are in the `data/` folder:
   - `transactionError_APM.csv`
   - `transaction_APM.csv`
3. Run all cells in order (each cell depends on the previous one)

**What this notebook does:**
- Merges two CSV files based on `appName`
- Converts Unix timestamps to readable format
- Aggregates data to minute-level intervals
- Creates complete time series with filled missing values

### Step 2: Forecasting

1. Open `src/forecast.ipynb` in VS Code
2. **Important**: Update the TimeGPT API credentials in the notebook:
   ```python
   nixtla_client = NixtlaClient(
       base_url="https://your-endpoint.eastus2.models.ai.azure.com",
       api_key="your-api-key"
   )
   ```
3. Run all cells in order

**What this notebook does:**
- Loads the processed minute-level data
- Visualizes the time series
- Performs forecasting with confidence intervals
- Generates prediction plots

### Step 3: Interpreting Results

The forecast output includes:
- **TimeGPT**: Point forecast (most likely value)
- **TimeGPT-lo-80**: Lower bound of 80% confidence interval
- **TimeGPT-hi-80**: Upper bound of 80% confidence interval
- **TimeGPT-lo-90**: Lower bound of 90% confidence interval
- **TimeGPT-hi-90**: Upper bound of 90% confidence interval

## 📄 File Descriptions

### Data Processing Files

- **`data_transform.ipynb`**: Main data preprocessing notebook
  - Merges transaction data
  - Timestamp conversion
  - Data aggregation and cleaning

- **`forecast.ipynb`**: Time series forecasting notebook
  - TimeGPT integration
  - Forecasting with confidence intervals
  - Visualization

### Data Files

- **Input Files**:
  - `transactionError_APM.csv`: Contains error transaction data
  - `transaction_APM.csv`: Contains general transaction data

- **Intermediate Files**:
  - `merged_transaction_data.csv`: Raw merged data
  - `merged_transaction_data_formatted.csv`: Formatted timestamps

- **Output Files**:
  - `processed_minutely_data.csv`: Final processed data ready for forecasting

## 🔧 Troubleshooting

### Common Issues

#### 1. Package Installation Errors

```bash
# If you get permission errors, try:
pip install --user pandas numpy nixtla zstandard

# If you get SSL errors, try:
pip install --trusted-host pypi.org --trusted-host pypi.python.org pandas numpy nixtla zstandard
```

#### 2. Kernel Not Found in VS Code

1. Press `Ctrl+Shift+P`
2. Type "Python: Select Interpreter"
3. Choose the correct Python environment
4. Restart VS Code if needed

#### 3. TimeGPT API Errors

- Ensure your API key is valid
- Check your internet connection
- Verify the base URL is correct

#### 4. Data File Errors

- Ensure all CSV files are in the correct `data/` directory
- Check file permissions
- Verify file formats and column names

#### 5. Memory Issues

If you encounter memory issues with large datasets:
- Reduce the time range in data processing
- Use data sampling techniques
- Increase system RAM or use cloud computing

### Performance Tips

1. **For large datasets**: Consider sampling data or processing in chunks
2. **For faster execution**: Use SSD storage and ensure sufficient RAM
3. **For API limits**: Be mindful of TimeGPT API rate limits


