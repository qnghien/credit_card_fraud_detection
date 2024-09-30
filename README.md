# Fraud Detection Model - IEEE-CIS Fraud Detection
![Fraud Detection Image](img/credit_fraud.jpeg)

## Project Overview
This project aims to build a robust fraud detection model for identifying high-risk credit card transactions. The dataset used for this project was collected from the **IEEE-CIS Fraud Detection Contest** on **Kaggle**, containing both transactional data and identity-related features. The objective was to predict fraudulent transactions using machine learning (ML) and deep learning (DL) techniques.

## Dataset
The dataset consists of two main components:
- **Transaction Data**: 394 factors related to online transactions.
- **Identity Data**: 41 factors related to the identity of the transactions (e.g., card information, address).

Due to the size and complexity of the dataset, data preprocessing involved partitioning the data based on relationships with the response variable and filtering out N/A values, which could not be accurately imputed.

### Key Variables:
- **TransactionDT**: Time delta from a given reference datetime (not an actual timestamp).
- **TransactionAMT**: Transaction amount in USD.
- **ProductCD**: Product code representing the transaction product.
- **Card1-Card6**: Payment card information, such as card type, issuer bank, country, etc.
- **Addr**: Address of the purchaser.
- **Dist**: Distance from the seller's location to the purchaser's location.
- **P_emaildomain**: Purchaser’s email domain.
- **C1-C14**: Count features representing the number of associated addresses, cards, etc. (actual meanings are masked for confidentiality).
- **D1-D15**: Timedelta variables representing intervals between transactions.
- **M1-M9**: Boolean match indicators (e.g., name match between card and address).
- **Vxxx**: Engineered features representing rankings, counts, and relationships.

## Assumptions:
1. **Distance Correlation**: The greater the distance between the purchaser's and the seller's locations, the higher the probability of fraud.
2. **Email Domain Suspicion**: Less popular email domains may be indicative of fraudulent behavior.
3. **Transaction Amount Decimal Places**: Suspicious transactions might have a non-standard number of decimal places in the transaction amount.
4. **Card Type**: The type of card used does not significantly influence fraud detection.

## Data Preprocessing:
- **Handling N/A Values**: N/A values were removed during aggregated calculations, as imputing them (with 0 or nearest values) could distort the results, given their transaction-specific nature.
- **Dropped Columns**: 
  - **Vxx** columns: Contained mostly null values and their meanings were unclear.
  - **Cxx** columns: Since their actual meanings were masked, these were excluded from the model.
  - **R_emaildomain**: Assumed that fraud is only related to the purchaser's information.
  
## Methodology
We used a variety of machine learning and deep learning techniques to build predictive models. The following techniques were applied:

- **Logistic Regression**: A baseline classification technique to identify the probability of fraud.
- **Decision Trees**: A non-linear model to capture complex interactions between variables.
- **XGBoost**: A gradient boosting algorithm to improve prediction accuracy and deal with imbalanced data.
- **Neural Networks**: A deep learning technique used to enhance model accuracy and performance.
  
### Model Evaluation:
- **K-fold Cross-Validation**: Used to evaluate all ML models (except Neural Networks) and ensure generalizability.
- **Imbalanced Data**: Given the high proportion of non-fraudulent transactions, the models were evaluated using **Macro F1-Score**—the harmonic mean of precision and recall metrics. This ensures that both classes (fraud and non-fraud) are treated equally during evaluation.

## Results and Final Model:
The final model was selected based on the one with the highest macro F1-score. The **Neural Network** model showed the best performance in predicting fraudulent transactions, improving accuracy beyond traditional ML models.

## Conclusion:
This project developed a powerful fraud detection system that can help identify high-risk transactions with high precision. By using both traditional and advanced models, we ensured that the system is adaptable to varying transaction patterns while maintaining accuracy in fraud detection.

## Future Work:
- Experiment with additional feature engineering techniques.
- Implement more sophisticated neural network architectures (e.g., LSTM, CNN) for potential improvement.
- Incorporate real-time fraud detection capabilities to handle evolving fraud patterns.

## Acknowledgments:
The dataset was provided by the **IEEE-CIS Fraud Detection Contest** hosted on **Kaggle**.
