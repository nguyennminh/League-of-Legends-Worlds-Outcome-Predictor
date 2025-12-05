# 🎮 League of Legends Worlds Match Outcome Predictor

A machine learning project that predicts the outcomes of League of Legends professional matches using historical data. The project trains two models (Logistic Regression and Random Forest) and provides predictions with confidence scores for head-to-head team matchups.

---

## 🎯 Overview

This project uses machine learning to predict League of Legends match outcomes based on:
- Team historical performance
- Recent form (last 5 games)
- Side advantage (Blue vs Red)
- Regional strength
- Champion picks
- Kill/Death statistics

The model is trained on professional League of Legends data and can predict upcoming matches with confidence scores.

---

## ✨ Features

- **Two ML Models**: Logistic Regression and Random Forest classifiers
- **Ensemble Predictions**: Combines both models for improved accuracy
- **Team Matchup Predictions**: Compare any two teams head-to-head
- **Comprehensive Visualizations**: 
  - Data exploration plots
  - Model performance comparison
  - ROC curves
  - Confusion matrices
  - Feature importance rankings
- **Detailed Statistics**: Shows team stats, win rates, and recent form

---

## 🔧 Requirements

### Python Version
- **Python 3.11** (Required)

### Libraries

Listed in the requirements.txt file

```
pandas
numpy
scikit-learn
seaborn
matplotlib
```

---

## 📦 Installation

### Step 1: Clone the Repository
```bash
git clone https://github.com/nguyennminh/League-of-Legends-Worlds-Outcome-Predictor.git
cd League-of-Legends-Worlds-Outcome-Predictor
```

### Step 2: Create Virtual Environment (Python 3.11)
**Make sure you have Python 3.11 installed on your system.**

**On macOS/Linux:**
```bash
python3.11 -m venv venv
source venv/bin/activate
```

**On Windows:**
```bash
python -m venv venv
venv\Scripts\activate
```

### Step 3: Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 4: Download Data
Download the League of Legends match data from Oracle Elixer's Google Drive. Link and Instructions in datasets/PLEASE READ

---

## 🚀 Usage

### 1. Process the Data 

First, in data_preprocessing.ipynb

⚠️ Make sure you have the datasets from the Oracle Exlixer's Google Drive downloaded and inside of datasets folder

Run the script to combine all csv file datasets residing in datasets folder into combined_dataset.csv

Click on - Run All Cells

### 2. Training the Model

Secondly, in model_training.ipynb

Run the main script to train both models:

Click on - Run All Cells

This will:
1. Load and preprocess the data
2. Engineer features
3. Train Logistic Regression and Random Forest models
4. Generate visualizations
5. Save trained models to disk
6. Show an example prediction

❗ For changing the train-test split years to correspond with your time range it will be under the Main Function

Find the section of code that has the variable test_year and change the test_year to your desired cutoff, under step - 5. Split Data

```python
# Use 2025 for test, everything else for train
        test_year = 2025
        train_df = df[df['year'] < test_year]
        test_df = df[df['year'] == test_year]
```

When deciding for a train-test split it is recommended to do 80% of the data for training and 20% of the data for testing.


### Making Predictions

#### Option 1: During Training
After the training completes, the script automatically shows available teams and makes an example prediction.

#### Option 2: In Python Script/Notebook
```python
# After training, use the returned objects
# There will be a list of available teams listed in the output with the corresponding index. Change team1 and team2 indexes for
# available_team list to change matchups

team1 = available_teams[0] # change to team wanted
team2 = available_teams[1] # change to team wanted
        
predict_team_matchup(team1, team2, best_model, df, feature_cols, scaler)
```

---

## 📊 Data

### Data Source
- **Oracle's Elixir**: Professional League of Legends match data
- Download: https://drive.google.com/drive/u/1/folders/1gLSw0RLjBbtaNy0dgnGQDAZOHIgCe-HH
- Website: https://oracleselixir.com/tools/downloads

### Data Requirements
The CSV file should contain the following columns:
- `teamname`: Team name
- `result`: Match outcome (1 = win, 0 = loss)
- `kills`, `deaths`, `assists`: Player/team statistics
- `side`: Blue or Red side
- `date`: Match date
- `year`: Year of the match
- `league`: League/tournament name
- `champion`: Champion picked
- Other statistics (gold, kills at different time marks, etc.)

### Data Structure
- Each match has multiple rows (one per player + team summary)
- The script filters for team-level data automatically
- Code supports all years - However currently it is only using datasets from years 2020 - 2025.

---

## 📈 Model Performance

### Evaluation Metrics
The models are evaluated using:
- **Accuracy**: Overall prediction correctness
- **AUC-ROC**: Area under the ROC curve
- **Precision/Recall**: Classification quality metrics
- **Confusion Matrix**: True/False positive/negative breakdown

### Typical Performance
- **Validation Accuracy**: 60-70%
- **AUC**: 0.65-0.75

**Note**: League of Legends has inherent randomness, and even professional analysts achieve ~60-65% accuracy. Predictions above 50% (random guessing) are considered successful.

---


## 💡 Examples

### Example Output: Team Matchup Prediction

```
======================================================================
Making example prediction...
======================================================================
PREDICTING: 100 Thieves vs Anyone's Legend
⚠️  Single model passed, wrapping in dictionary...

======================================================================
PREDICTING: 100 Thieves vs Anyone's Legend
======================================================================

100 Thieves Stats:
  Recent Win Rate: 20.00%
  Avg Kills: 12.6
  Overall Win Rate: 33.33%

Anyone's Legend Stats:
  Recent Win Rate: 40.00%
  Avg Kills: 15.2
  Overall Win Rate: 60.00%

======================================================================
PREDICTION RESULTS:
======================================================================

Model:
  100 Thieves: 16.2%
  Anyone's Legend: 83.8%
  Predicted Winner: Anyone's Legend (Confidence: 83.8%)
======================================================================
```

## 🙏 Acknowledgments

- **Oracle's Elixir** for providing comprehensive League of Legends esports data
- **Riot Games** for League of Legends
- **scikit-learn** for machine learning tools
- **pandas** and **numpy** for data manipulation

---

## 📧 Contact

For questions or feedback, please open an issue on GitHub.

---

## ⚠️ Disclaimer

This project is for educational purposes only. Match predictions are based on historical data and should not be used for betting or gambling. League of Legends is a trademark of Riot Games, Inc. This project is not affiliated with or endorsed by Riot Games.

---

**Built with ❤️ for the League of Legends esports community**
