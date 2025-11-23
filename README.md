# pollution-src-classify
🌫️ Pollution Source Classification Using Machine Learning
This project builds a rule-guided + machine learning hybrid system to classify the dominant pollution source in Delhi using publicly available AQI sensor data.
It demonstrates data engineering, domain-based labeling, feature extraction, training a Random Forest classifier, and evaluating model performance.


📘 Project Overview
The dataset contains air-quality readings such as:


PM2.5


PM10


CO


NO, NO₂


O₃


SO₂


NH₃


Timestamps


Since datasets usually don’t include the source of the pollution, this project uses domain knowledge to assign labels, and then trains an ML model to classify pollution sources.
The pollution categories include:


Traffic


Industrial


Dust


Accident / Fire Event



📂 Dataset
The dataset (delhi_aqi.csv) contains hourly pollution metrics for Delhi.
Columns include:


date


pm2_5, pm10


co, no, no2


o3, so2, nh3



🧠 How Sources Are Labeled (Rule-Based)
Since the dataset has no labels, we generate them using environmental rules:
Traffic


Rush hours (7–10 AM, 5–8 PM)


High NO and CO levels


Industrial


Late nighttime hours (0–4 AM)


High SO₂ peaks


Dust


PM10 much higher than PM2.5


Indicates construction or road dust


Accident / Fire


Sudden spike in PM2.5 beyond the rolling mean


All rows labeled as "Other" are discarded.

🛠️ Feature Engineering
Additional features created:


Time features: Hour, day of week


Ratios: PM10/PM2.5, NO/CO


Rolling averages: PM2.5 rolling mean


Differences: PM2.5 day-to-day delta


This improves model interpretability and classification performance.

🤖 Machine Learning Model
A Random Forest Classifier with:


200 trees


Stratified train-test split


80/20 split


Evaluation using classification report


Final model is saved as:
rf_pollution_source.pkl


📈 Results & Model Evaluation
The script prints:


Precision


Recall


F1-score


Class-wise breakdown


Feature importance is visualized to show which pollution components matter most.
Examples of expected top features:


PM2.5


PM10


SO₂


NO/CO ratio


PM2.5 rolling averages



🚀 How to Run
1. Install requirements:
pip install pandas numpy scikit-learn matplotlib joblib

2. Place dataset in the root:
delhi_aqi.csv

3. Run the script:
python pollution_source_classification.py

Output:


Labeled dataset


Trained Random Forest


Feature importance chart


Saved model file







🚀 Ways to Improve (Future Work)
If you want to extend this project, here are strong improvements:
1. Use Additional Features
Add:


Wind speed


Humidity


Temperature


Traffic volume


Satellite aerosol data


This drastically improves accuracy.
2. Replace Rule-Based Labeling with Clustering
Instead of hard rules:


Use K-Means, DBSCAN, or Gaussian Mixtures


Then annotate clusters manually


This creates more realistic labels.
3. Try Advanced Models


Gradient Boosting (XGBoost, LightGBM, CatBoost)


Time-series models like LSTM or Temporal Fusion Transformers


4. Improve Accident/Fire Detection
Use:


Change-point detection


Anomaly detection models


Wavelet transforms


5. Expand Dataset to More Cities
This improves generalization.
6. Deploy a Live Dashboard
Using Streamlit:


Upload CSV


Predict pollution source


Show feature contribution





