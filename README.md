# Porter Delivery Time Estimation

## Project Overview

This project focuses on predicting delivery times for Porter, India's largest marketplace for intra-city logistics. Using machine learning techniques, this project aims to accurately estimate delivery time based on various logistical, geographical, and order-related features. By providing a precise prediction of delivery times, the model helps optimize logistics operations and improves customer satisfaction.

---

## Dataset

The dataset contains various features related to delivery operations, order specifics, and dashers (delivery personnel). It was preprocessed and cleaned to remove inconsistencies, null values, and irrelevant data.

### Key Features:

| **Feature**                                  | **Description**                                                                 |
|----------------------------------------------|---------------------------------------------------------------------------------|
| `market_id`                                  | ID representing the city or market where the delivery occurred.                 |
| `store_primary_category`                     | Main category of the store from which the order was placed.                     |
| `order_protocol`                             | Protocol followed during order processing (e.g., mobile, website).              |
| `total_items`                                | Total number of items in the order.                                             |
| `subtotal`                                   | Total price of all items before taxes and fees.                                 |
| `num_distinct_items`                         | Number of unique items in the order.                                            |
| `min_item_price`                             | Minimum price of a single item in the order.                                    |
| `max_item_price`                             | Maximum price of a single item in the order.                                    |
| `total_onshift_dashers`                      | Number of dashers (delivery personnel) on shift during the order.               |
| `total_busy_dashers`                         | Number of dashers who were busy when the order was placed.                      |
| `total_outstanding_orders`                   | Number of pending orders in the system when this order was placed.              |
| `estimated_store_to_consumer_driving_duration`| Estimated driving time from store to consumer (in seconds).                     |
| `created_year`, `created_month`, `created_day`, `created_hour` | Date and time-related features extracted from the order creation timestamp.      |
| `delivery_year`, `delivery_month`, `delivery_day`, `delivery_hour` | Date and time-related features extracted from the actual delivery timestamp.     |
| `delivery_time_minutes`                      | Target variable: Actual delivery time in minutes.                               |

---

## Algorithms Used

Several machine learning algorithms were used to predict delivery times:

1. **Decision Tree Regressor**
   - Simple model that splits data based on decision rules derived from the features.
   
2. **Random Forest Regressor**
   - An ensemble of decision trees that provides robust predictions by averaging multiple trees.

3. **Linear Regression**
   - A linear model used to estimate the relationship between the features and the delivery time.

4. **Gradient Boosting Regressor**
   - A boosting algorithm that builds an ensemble model in a stage-wise fashion, optimizing performance.

---

## Steps for Project Execution

1. **Data Preprocessing:**
   - Convert datetime columns to usable numerical features such as year, month, day, and hour.
   - Handle missing values and outliers.
   - Standardize and scale the numeric features.

2. **Feature Engineering:**
   - Extract date and time features from `created_at` and `actual_delivery_time`.
   - Removed unnecessary columns like raw timestamps after feature extraction.

3. **Model Building:**
   - Train-test split of the dataset (80%-20%).
   - Trained models using various regressors (Random Forest, Decision Tree, etc.).
   - Evaluated model performance using metrics like MSE, MAE, and R-squared.

4. **Model Evaluation:**
   - Model performance was evaluated using the following metrics:
     - **Mean Squared Error (MSE)**
     - **Mean Absolute Error (MAE)**
     - **R-Squared (R²)**

---

## Results

- The **Random Forest Regressor** yielded the best performance with:
  - Mean Squared Error (MSE): 3.67
  - Mean Absolute Error (MAE): 1.41
  - R-squared (R²): 0.95
  
These results indicate that the model can predict delivery times with high accuracy and minimal error.

---

## How to Use

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/porter-delivery-estimator.git
   cd porter-delivery-estimator

2. Install Dependencies
   ```bash
   pip install -r requirements.txt

3. Run the model
   ```bash
   python train_model.py

4. Predict Delivery Time
   ```bash
   y_new = rf_regressor.predict(ms.transform([[market_id, store_category, order_protocol, total_items, subtotal, ...]]))
   print(f'Estimated Delivery Time: {y_new} minutes')
      
