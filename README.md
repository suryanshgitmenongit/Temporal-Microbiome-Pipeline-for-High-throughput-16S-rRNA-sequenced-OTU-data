# Temporal-Microbiome-Pipeline-for-High-throughput-16S-rRNA-sequenced-OTU-data

TEMPHOS-16S is a comprehensive analytical pipeline designed for temporal analysis of microbiome data generated from high-throughput 16S rRNA sequencing. The pipeline integrates time series analysis, ecological metrics, and machine learning approaches to provide deep insights into microbial community dynamics.

You can also run this directly on collab:


https://colab.research.google.com/drive/1YkZOvJPm_ja36JKeDmiJnSqZ_p70ffxy?usp=sharing#scrollTo=gxbQ-MHJ2oue {Streamlit App}


OR


https://colab.research.google.com/drive/1Qe06MD86ADzqSefDHMbl8CiP8sxDP1Qd?usp=sharing {pipeline overview}

## 🔑 Key Features

### Time Series Analysis
- Diel pattern detection and visualization
- Time derivatives of OTU abundances
- Smoothed volatility analysis using Savitzky-Golay filtering
- Time series decomposition (trend, seasonal, residual components)

### Ecological Metrics
- Alpha diversity calculation (Shannon index)
- Beta diversity analysis (Bray-Curtis dissimilarity)
- Principal Coordinate Analysis (PCoA)
- Taxonomic composition tracking

### Machine Learning Integration
- Random Forest temporal prediction
- SHAP (SHapley Additive exPlanations) value analysis
- Feature importance evaluation

### Python Dependencies
```
pandas
numpy
matplotlib
seaborn
scipy
scikit-learn
plotly
networkx
statsmodels
scikit-bio
shap
```

## 📊 Input Data Requirements

### OTU Table Format
- CSV file format
- Rows: OTUs (features)
- Columns: Samples
- Values: Read counts or relative abundances

Example:
```csv
OTU_ID,Sample1,Sample2,Sample3,...
OTU_1,123,345,567,...
OTU_2,234,456,678,...
```

### Metadata Format
- CSV file format
- Must include:
  - `sample_id`: Unique sample identifier
  - `ind_time`: Time point in decimal format
- Additional metadata columns are supported

Example:
```csv
sample_id,ind_time,temperature,pH,...
Sample1,0.25,22.3,7.2,...
Sample2,0.50,22.5,7.1,...
```

### Custom Analysis

```python
# Run specific analyses
pipeline.diel_patterns_analysis()
pipeline.taxonomic_composition(top_n=15)
pipeline.time_derivative_analysis()
```

## 📈 Output Files

The pipeline generates the following visualization files:

```
generated/
├── diel_patterns_{uuid}.png       # Daily patterns of top OTUs
├── taxa_abundance_{uuid}.png      # Abundance heatmap
├── alpha_diversity_{uuid}.png     # Shannon diversity plots
├── beta_diversity_{uuid}.png      # PCoA ordination plots
├── taxonomic_composition_{uuid}.png# Relative abundance plots
├── top_of_30_{uuid}.png          # Top 30 OTUs analysis
├── top_of_5_{uuid}.png           # Detailed top 5 OTUs
├── smoothed_volatility_{uuid}.png # Volatility analysis
└── timeseries_decomposition_{uuid}.png # Time series components
```

## 🔧 Customization Options

### Smoothing Parameters
```python
pipeline.smoothed_volatility_analysis(
    window_length=5,  # Adjust smoothing window
    polyorder=2       # Polynomial order
)
```

### Visualization Options
```python
pipeline.taxonomic_composition(
    top_n=10,        # Number of top taxa to display
    filename='custom_output.png'
)
```

<img width="1187" alt="Screenshot 2024-11-20 at 2 11 28 PM" src="https://github.com/user-attachments/assets/4585c5b7-edc9-456f-ad15-1280b22c46bd">

<img width="951" alt="Screenshot 2024-11-20 at 2 12 05 PM" src="https://github.com/user-attachments/assets/f048b8bd-09dc-4463-b77c-493e6ba8f1a6">

<img width="889" alt="Screenshot 2024-11-20 at 2 13 20 PM" src="https://github.com/user-attachments/assets/81517715-9ae9-4511-8d3d-6dcbc585a3d3">

<img width="890" alt="Screenshot 2024-11-20 at 2 13 38 PM" src="https://github.com/user-attachments/assets/14384500-7984-45e1-83b9-a5282cca2ee3">

<img width="570" alt="Screenshot 2024-11-20 at 2 13 54 PM" src="https://github.com/user-attachments/assets/3a82e961-7cc7-4336-91ef-a26950f7d3c3">
