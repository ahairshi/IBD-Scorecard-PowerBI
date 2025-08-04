# Complete Setup Documentation

## Project: IBD Scorecard Power BI Dashboard

This document contains the complete setup process for creating a Power BI dashboard from AWS S3 data.

## Prerequisites Installed
- AWS CLI v2.28.1
- Python 3.12.10
- GitHub CLI v2.76.2
- Git v2.44.0

## Key Setup Commands

### 1. AWS CLI Installation & Configuration
```powershell
# Install AWS CLI
winget install Amazon.AWSCLI

# Configure AWS credentials (interactive)
aws configure

# List S3 buckets
aws s3 ls

# Explore bucket structure
aws s3 ls s3://scorecard/ --recursive
```

### 2. Data Download (Last 2 Years)
```powershell
# Create local data directory
New-Item -ItemType Directory -Force -Path ".\PowerBI_Data"

# Download 2023 data
aws s3 sync s3://scorecard/IBD/2023/ .\PowerBI_Data\2023\ --exclude "*" --include "*.parquet"

# Download 2024 data
aws s3 sync s3://scorecard/IBD/2024/ .\PowerBI_Data\2024\ --exclude "*" --include "*.parquet"

# Download 2025 data
aws s3 sync s3://scorecard/IBD/2025/ .\PowerBI_Data\2025\ --exclude "*" --include "*.parquet"
```

### 3. Data Verification
```powershell
# List downloaded files
Get-ChildItem -Path .\PowerBI_Data -Recurse -Name | Sort-Object

# Check file sizes and count
Get-ChildItem -Path .\PowerBI_Data -Recurse -Include *.parquet | Measure-Object -Property Length -Sum
```

### 4. Project Setup
```powershell
# Create project directory
New-Item -ItemType Directory -Force -Path ".\IBD-Scorecard-PowerBI"

# Copy setup files
Copy-Item -Path "PowerBI_Setup_Guide.txt" -Destination ".\IBD-Scorecard-PowerBI\"
Copy-Item -Path "PowerQuery_Script.txt" -Destination ".\IBD-Scorecard-PowerBI\"
Copy-Item -Path "DAX_Measures.txt" -Destination ".\IBD-Scorecard-PowerBI\"
```

### 5. Git Repository Setup
```powershell
# Navigate to project directory
cd "C:\Users\ahamedirshad\IBD-Scorecard-PowerBI"

# Initialize Git repository
git init

# Add all files
git add .

# Initial commit
git commit -m "Initial commit: IBD Scorecard Power BI project setup"
```

### 6. GitHub Setup
```powershell
# Install GitHub CLI
winget install GitHub.cli

# Authenticate with GitHub
gh auth login --web

# Create repository and push
gh repo create IBD-Scorecard-PowerBI --public --source=. --remote=origin
git branch -M main
git push -u origin main
```

## Data Summary
- **Total Files**: 29 parquet files
- **Total Size**: ~22 MB
- **Time Range**: January 2023 - May 2025
- **Data Structure**: Monthly files organized by year (YYYYMM format)
- **File Format**: Parquet (optimized for Power BI)

## File Structure
```
IBD-Scorecard-PowerBI/
├── README.md                    # Project documentation
├── PowerBI_Setup_Guide.txt      # Step-by-step Power BI setup
├── PowerQuery_Script.txt        # M script for data transformation
├── DAX_Measures.txt            # Analytics measures
├── .gitignore                  # Git ignore rules
├── command_history.csv         # Complete command history
├── Setup_Commands.txt          # Readable command format
└── SETUP_DOCUMENTATION.md     # This file
```

## Next Steps
1. **Open Power BI Desktop**
2. **Follow PowerBI_Setup_Guide.txt** for data loading
3. **Use PowerQuery_Script.txt** for transformations
4. **Implement DAX_Measures.txt** for analytics
5. **Create visualizations** based on requirements

## Repository Information
- **GitHub URL**: https://github.com/ahairshi/IBD-Scorecard-PowerBI
- **Owner**: ahairshi
- **Visibility**: Public
- **Remote**: origin (https://github.com/ahairshi/IBD-Scorecard-PowerBI.git)

## Environment Details
- **OS**: Windows 11 ARM64
- **Shell**: PowerShell 5.1.22621.5624
- **Working Directory**: C:\Users\ahamedirshad\IBD-Scorecard-PowerBI
- **Setup Date**: August 4, 2025

## Support Files
- Raw command history available in `command_history.csv`
- Formatted commands available in `Setup_Commands.txt`
- All scripts are ready to use and documented

---
*This documentation captures the complete setup process for reproducibility and future reference.*
