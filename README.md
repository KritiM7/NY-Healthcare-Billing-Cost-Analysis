# Healthcare-Cost-Predictor
Predicting healthcare costs is notoriously difficult because patient data is a mix of categories (like severity of illness) and numbers (like facility IDs). For this project, I built a robust machine learning pipeline to automate these predictions using the New York State Department of Health dataset.

Why I used a Pipeline: Instead of cleaning the data manually every time, I used a Scikit-Learn Pipeline. This ensures that the StandardScaler (for numbers) and the OneHotEncoder (for categories) are applied consistently to both training and testing data, preventing "data leakage".

The Technical Highlights:

The Model: I chose Ridge Regression. This is more advanced than basic linear regression because it uses L2 Regularization to prevent the model from becoming too sensitive to outliers in the data.
Cross-Validation: I didn't just pick a random setting; I tested multiple "alpha" values ($0.1$ to $250$) using 5-fold Cross-Validation to find the most stable version of the model.
Performance: The model achieved an $R^2$ of 0.708 on the hold-out set, meaning it explains over 70% of the variance in patient costs.
Error Metric: The Mean Absolute Error (MAE) was $8,043, which provides a realistic window for financial planning in a hospital setting.

How to use:
Open the .ipynb file in Colab.
The notebook processes the SPARCS_De-Identified dataset.
Run the pipeline to see the ColumnTransformer in action and the final error metrics.
