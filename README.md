# IBD Scorecard Power BI Dashboard

## Project Overview
This repository contains the setup files and documentation for creating a Power BI dashboard to analyze IBD (Inflammatory Bowel Disease) Scorecard data from S3.

## Data Source
- **Source**: AWS S3 Bucket (`scorecard`)
- **Format**: Parquet files
- **Time Range**: 2023-2025 (29 months of data)
- **Total Size**: ~22 MB
- **Structure**: Monthly files organized by year (YYYYMM format)

## Files in This Repository

### 📋 Setup Documentation
- **`PowerBI_Setup_Guide.txt`** - Complete step-by-step guide to set up Power BI dashboard
- **`PowerQuery_Script.txt`** - M script for Power Query transformations
- **`DAX_Measures.txt`** - Collection of DAX measures for analytics

### 🗂️ Data Structure
```
PowerBI_Data/
├── 2023/
│   ├── 202301_ibd_scorecard.parquet
│   ├── 202302_ibd_scorecard.parquet
│   └── ... (12 monthly files)
├── 2024/
│   ├── 202401_ibd_scorecard.parquet
│   ├── 202402_ibd_scorecard.parquet
│   └── ... (12 monthly files)
└── 2025/
    ├── 202501_ibd_scorecard.parquet
    ├── 202502_ibd_scorecard.parquet
    └── ... (5 monthly files so far)
```

## Quick Start

### Prerequisites
- Power BI Desktop
- AWS CLI configured (for data downloads)
- Access to S3 bucket `scorecard`

### Setup Steps
1. **Download Data**: Use AWS CLI to sync S3 data locally
2. **Open Power BI**: Follow the setup guide to load data
3. **Apply Transformations**: Use the provided M script
4. **Add Measures**: Implement DAX measures for analytics
5. **Create Visuals**: Build dashboard components

### Data Download Command
```bash
# Download last 2 years of data
aws s3 sync s3://scorecard/IBD/2023/ ./PowerBI_Data/2023/ --include "*.parquet"
aws s3 sync s3://scorecard/IBD/2024/ ./PowerBI_Data/2024/ --include "*.parquet"
aws s3 sync s3://scorecard/IBD/2025/ ./PowerBI_Data/2025/ --include "*.parquet"
```

## Dashboard Features

### 📊 Key Metrics
- Current Month Performance
- Month-over-Month Changes
- Year-over-Year Comparisons
- Moving Averages (3, 6, 12 months)
- Performance Trends

### 📈 Visualizations
- KPI Cards for key metrics
- Line charts for trend analysis
- Column charts for monthly comparisons
- Performance distribution histograms
- Detailed data tables with drill-through

### 🎯 Analytics Capabilities
- Time intelligence measures
- Statistical analysis (std dev, median, etc.)
- Performance ranking
- Conditional formatting
- Trend indicators

## File Descriptions

### PowerBI_Setup_Guide.txt
Complete instructions for:
- Loading data from folder
- Power Query transformations
- Creating visualizations
- Dashboard layout recommendations

### PowerQuery_Script.txt
Ready-to-use M script that:
- Combines all parquet files
- Extracts dates from filenames
- Adds time dimension columns
- Cleans and structures data

### DAX_Measures.txt
Comprehensive collection of measures including:
- Basic aggregations
- Time comparisons
- Moving averages
- Statistical measures
- Performance indicators

## Data Refresh Strategy

### Manual Refresh
1. Download new parquet files to local folder
2. Refresh Power BI dataset
3. New files automatically included

### Automated Refresh (Future)
- Direct S3 connection via Power BI Gateway
- Scheduled refresh configuration
- Real-time dashboard updates

## Project Timeline
- **Data Period**: January 2023 - May 2025
- **Setup Date**: August 2025
- **Files**: 29 parquet files
- **Total Records**: ~13 million (estimated)

## Technical Notes
- Parquet format provides excellent compression and performance
- Monthly partitioning enables efficient filtering
- Date extraction from filename maintains chronological order
- Power BI handles large datasets efficiently with proper modeling

## Support
For questions about setup or modifications, refer to the detailed documentation in each text file.

---
*Created with AWS S3, Power BI, and automated data processing*
