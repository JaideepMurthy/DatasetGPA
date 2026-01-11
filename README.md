[# DatasetGPA - AI-Powered CSV Dataset Quality Analyzer

<div align="center">

[![GitHub](https://img.shields.io/badge/github-%23121011.svg?style=for-the-badge&logo=github&logoColor=white)](https://github.com/JaideepMurthy/DatasetGPA)
[![Vercel](https://img.shields.io/badge/vercel-%23000000.svg?style=for-the-badge&logo=vercel&logoColor=white)](https://https://aistudio.google.com/apps/drive/1mX5KMIykNg0G6kjht_7CTSjwlSzq2yVR-jaideep-murthys-projects.vercel.app)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

**Instantly analyze CSV datasets and detect quality issues before training models**

[🚀 Live Demo](#-try-it-out) • [📖 How It Works](#-how-it-works) • [⚙️ Features](#-features) • [🛠️ Tech Stack](#-tech-stack)

</div>

---

## The Problem

As machine learning engineers, we've all been there:
- Spending **hours debugging datasets** instead of building models
- Discovering **data quality issues too late** (after training fails)
- Missing **class imbalance, missing values, data leakage, outliers**
- Wasting compute on **bad datasets** that should've been caught immediately

Dataset quality issues cause **60-70% of ML failures**, yet most teams lack tools to catch them early.

## The Solution

**DatasetGPA** is a browser-based tool that instantly analyzes your CSV datasets and tells you exactly what's wrong—**before you waste time training**.

✨ **100% client-side • Zero backend • Works in any browser**

### Key Benefits

- ⚡ **Instant Analysis**: Analyze datasets in seconds
- 🧠 **AI-Powered Insights**: Claude API generates actionable recommendations
- 📊 **Comprehensive Checks**: 6 different quality metrics
- 🔒 **Privacy First**: Your data never leaves your browser
- 🎯 **Saves 2-5 hours per dataset**: Automates quality checks
- 🚀 **Zero Setup**: Just upload and analyze

---

## ✨ Features

### 1. **Missing Value Detection**
Column-by-column analysis of missing data patterns with percentage calculations

### 2. **Outlier Identification**
IQR-based statistical outlier detection for numeric features

### 3. **Class Imbalance Detection**
Identifies severe class distribution problems (>10:1 ratio)

### 4. **Data Leakage Warnings**
Flags suspicious column names and detects duplicate columns

### 5. **Health Score (0-100)**
Comprehensive dataset quality score with:
- Missing value impact
- Imbalance severity
- Outlier prevalence
- Leakage risks

### 6. **AI-Powered Recommendations**
Claude API generates specific, actionable suggestions:
- "Consider SMOTE for class balancing"
- "Remove rows with >30% missing values"
- "Investigate Column X for data leakage"

---

## 🚀 Try It Out

### Live Demo
[**Launch DatasetGPA**](https://ai.studio/apps/drive/1mX5KMIykNg0G6kjht_7CTSjwlSzq2yVR?fullscreenApplet=true)

### Quick Start (3 steps)

1. **Open the app** → No installation required
2. **Drag & drop your CSV** → Or click to select
3. **Get instant analysis** → Health score + recommendations

### Example Datasets

Try with these popular datasets:
- [Titanic Dataset](https://www.kaggle.com/c/titanic/data) - Class imbalance + missing values
- [Iris Dataset](https://archive.ics.uci.edu/ml/datasets/iris) - Clean data baseline
- [Credit Card Fraud](https://www.kaggle.com/datasets/mlg-ulb/creditcardfraud) - Extreme imbalance

---

## 🛠️ Tech Stack

### Frontend
- **React** - UI framework
- **Tailwind CSS** - Styling
- **Lucide React** - Icons
- **Papa Parse** - CSV parsing

### API & Cloud
- **Claude API** - AI recommendations
- **Vercel** - Deployment

### Architecture
- **100% Client-side** - No backend needed
- **CDN Libraries** - Fast load times
- **Browser APIs** - FileReader, localStorage

```html
<!-- All dependencies loaded from CDN -->
<script src="https://unpkg.com/react"></script>
<script src="https://unpkg.com/papaparse"></script>
<script src="https://cdn.tailwindcss.com"></script>
```

---

## 🏗️ How It Works

### Data Flow

```
CSV Upload
    ↓
Papa Parse (CSV → JSON)
    ↓
Analysis Engine (6 checks)
    ├── Missing Values
    ├── Outliers (IQR)
    ├── Class Imbalance
    ├── Data Leakage
    ├── Duplicates
    └── Numeric Detection
    ↓
Health Score Calculation
    ↓
Claude API (Optional)
    ↓
UI Rendering
```

### Analysis Functions

1. **Missing Value Analysis**
   ```javascript
   Checks: NULL, undefined, 'NA', 'NaN', empty strings
   Output: % missing per column
   ```

2. **Outlier Detection**
   ```javascript
   Method: Interquartile Range (IQR)
   Formula: Outliers = values outside [Q1-1.5*IQR, Q3+1.5*IQR]
   ```

3. **Class Imbalance Check**
   ```javascript
   Calculates: Max/Min class ratio
   Threshold: Ratio > 10:1 = Severe imbalance
   ```

4. **Data Leakage Detection**
   ```javascript
   Suspicious patterns:
   - Column names: 'target', 'label', 'id', 'prediction'
   - Duplicate columns (identical values)
   ```

---

## 📊 Health Score Calculation

```
Base Score: 100

- Missing values:    -30 points (max)
- Class imbalance:   -15 points
- Outliers:          -20 points (max)
- Data leakage:      -5 points (per warning)

Final: Max(0, score)
```

### Score Interpretation
- 🟢 **70-100**: Excellent - Ready to train
- 🟡 **50-70**: Caution - Address issues before training
- 🔴 **<50**: Critical - Significant quality issues

---

## 🔌 API Integration (Claude)

### Optional: Enable AI Insights

1. Get API key from [Anthropic](https://console.anthropic.com)
2. Click "Generate AI Insights" in the app
3. Paste your API key (stored locally only)
4. Get smart recommendations

```javascript
// Example recommendation
"Class imbalance detected (20:1 ratio). 
Consider SMOTE oversampling or class weights.
Target class represents only 4.7% of data."
```

---

## 📁 Project Structure

```
DatasetGPA/
├── index.html          # Complete React app (single file)
│   ├── <head>         # CDN imports, Tailwind
│   ├── <body>         # React root
│   └── <script>       # React component code
├── README.md          # This file
└── .git/              # Version control
```

### Why Single File?
- ✅ No build process needed
- ✅ Easy deployment (drop on any server)
- ✅ CDN for all dependencies
- ✅ Fast and simple

---

## 🚀 Deployment

### Deploy Your Own (30 seconds)

1. **Fork this repository**
   ```bash
   git clone https://github.com/YourUsername/DatasetGPA.git
   ```

2. **Deploy to Vercel (Recommended)**
   ```bash
   npm install -g vercel
   vercel
   ```

3. **Or Deploy to Netlify**
   - Connect GitHub repo
   - Auto-deploys on push
   - Free tier available

4. **Share your link!**
   ```
   https://yourdeployment.vercel.app
   ```

---

## 📈 Performance

- **Small datasets** (<1MB): <1 second
- **Medium datasets** (1-10MB): 1-3 seconds
- **Large datasets** (10-100MB): 3-10 seconds
- **Sampling**: Auto-samples if >10K rows for speed

---

## 🛡️ Privacy & Security

✅ **100% Client-side**
- Your data NEVER leaves your browser
- No server processing
- No data logging

✅ **localStorage for API key**
- API key stored locally only
- Clear anytime in settings
- Never sent to third parties

---

## 🔄 Future Roadmap

- [ ] Correlation heatmaps
- [ ] Automatic data fixing suggestions
- [ ] Weights & Biases integration
- [ ] Streaming for large files
- [ ] Export to Pandas/Python
- [ ] Team collaboration features
- [ ] Dataset comparison
- [ ] SQL database support

---

## 🤝 Contributing

Contributions welcome! Areas:

- **Feature requests**: [GitHub Issues](https://github.com/JaideepMurthy/DatasetGPA/issues)
- **Bug reports**: Describe the issue + dataset example
- **UI improvements**: UX suggestions
- **Analysis enhancements**: New quality metrics

```bash
git clone https://github.com/JaideepMurthy/DatasetGPA.git
cd DatasetGPA
# Edit index.html
git push origin feature/your-feature
```

---

## 📝 License

MIT License - Feel free to use commercially

---

## 🎓 Built For

**Alameda Hacks 2026** - A 10-day hackathon for building impactful tools

---

## 💡 Why DatasetGPA?

**GPA** = General Purpose Analyzer

Just like how GPA measures academic performance, DatasetGPA measures dataset health.

---

## 📞 Support & Feedback

- 🐛 **Bug reports**: [GitHub Issues](https://github.com/JaideepMurthy/DatasetGPA/issues)
- 💬 **Feedback**: Suggestions welcome!
- 🌟 **Like it?** Star this repo!

---

## 🙏 Acknowledgments

- Claude API for intelligent recommendations
- Papa Parse for robust CSV handling
- Vercel for seamless deployment
- Tailwind CSS for beautiful styling

---

**Built with ❤️ by Jaideep Murthy**

[Try DatasetGPA →](https://https://aistudio.google.com/apps/drive/1mX5KMIykNg0G6kjht_7CTSjwlSzq2yVR-jaideep-murthys-projects.vercel.app)
](https://https://aistudio.google.com/apps/drive/1mX5KMIykNg0G6kjht_7CTSjwlSzq2yVR-jaideep-murthys-projects.vercel.app/)
