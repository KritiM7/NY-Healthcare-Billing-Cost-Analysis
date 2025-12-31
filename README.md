# Healthcare-Cost-Predictor

Predicting healthcare costs is a huge challenge because the data is "noisy"—you have different hospitals, various illness severities, and hundreds of different types of treatments. I wanted to see if I could build a model that looks at over 2.1 million patient records and finds the patterns in how people are billed in New York State.
Unlike my other projects that were about categories (like Spam vs. Not Spam), this project is about scale. I had to figure out how to pull an 800MB dataset directly into the cloud and process it without crashing the system.

How I Built It:
I didn't just throw the data into an algorithm. I built a Scikit-Learn Pipeline to handle the heavy data:
Because the file was so large, I used gdown to bypass Google's "Virus Scan" block and low_memory=False to make sure the computer could read all 36 columns correctly.

The Pipeline: I used a ColumnTransformer so the model could "see" both numbers (like Facility IDs) and categories (like Severity of Illness) at the same time.

Ridge Regression (The "Smart" Choice): Instead of a basic regression, I used RidgeCV. It’s a more advanced model that uses a "penalty" (called Alpha) to make sure it doesn't get distracted by outliers. My model found that an Alpha of 100.0 was the "sweet spot" for accuracy.

The Results:
R^2 Score: 0.708 — This means my model explains about 71% of why medical costs change. In a dataset this massive and messy, 71% is a very strong result.
Mean Absolute Error: $8,043 — On average, the model's prediction is within about $8k of the actual bill. When you consider some hospital bills are hundreds of thousands of dollars, this is a solid window for financial planning.

How to Run:
Open medical_treatment_cost.ipynb in Google Colab.
Hit Run All.
The script will automatically install gdown, pull the 2.1 million rows, and train the model.
