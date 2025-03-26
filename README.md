# Ecommerce Product Recommendation System

## Overview
The **E-commerce Recommendation System** is a machine learning-based project that provides personalized product recommendations to users based on their browsing and purchase history. The system utilizes **collaborative filtering** and **content-based filtering** algorithms to analyze user behavior and generate relevant recommendations. This project aims to:
- Improve the overall shopping experience for users.
- Increase sales for e-commerce businesses.

## Dataset
The dataset used is an **Amazon dataset** containing user ratings for electronic products. The dataset does not have any headers. To avoid biases, each product and user is assigned a unique identifier instead of using their name or any other potentially biased information.


## Approach
### 1) Rank-Based Product Recommendation
#### **Objective:**
- Recommend products with the highest number of ratings.
- Target new customers with the most popular products.
- Solve the **Cold Start Problem**.

#### **Outputs:**
- Recommend the **top 5 products** with at least **50/100 minimum ratings**.

#### **Approach:**
1. Calculate the **average rating** for each product.
2. Calculate the **total number of ratings** for each product.
3. Create a DataFrame using these values and sort it by average rating.
4. Write a function to get **'n' top products** with a specified minimum number of interactions.

---

### 2) Similarity-Based Collaborative Filtering
#### **Objective:**
- Provide **personalized and relevant recommendations** to users.

#### **Outputs:**
- Recommend **top 5 products** based on interactions of similar users.

#### **Approach:**
1. Convert `user_id` to integer values (0 to 1539) for convenience.
2. **Find similar users:**
   - Compute the **cosine similarity score** between users.
   - Extract similar users and their similarity scores.
   - Remove the original user from the list.
3. **Recommend products to users:**
   - Identify **products the user has interacted with**.
   - Find **'n' products** that similar users have interacted with but the original user has not.
   - Return the **recommended products**.

---

### 3) Model-Based Collaborative Filtering
#### **Objective:**
- Provide personalized recommendations based on past behavior and preferences.
- Address challenges of **sparsity and scalability** in collaborative filtering.

#### **Outputs:**
- Recommend **top 5 products** for a particular user.

#### **Approach:**
1. Convert the matrix of **product ratings** into a **CSR (Compressed Sparse Row) matrix** to save memory.
2. Perform **Singular Value Decomposition (SVD)** to reduce the matrix to **50 latent features**.
3. Calculate **predicted ratings** using SVD.
4. Store predicted ratings in a DataFrame.
5. Write a function to **recommend products**:
   - Retrieve user's ratings and predicted ratings.
   - Filter out products already rated by the user.
   - Sort by predicted ratings and return **top recommendations**.

#### **Model Evaluation:**
1. Calculate the **average actual rating** and **average predicted rating**.
2. Compute the **Root Mean Squared Error (RMSE)** to evaluate the SVD model:
   - RMSE is calculated as:
     \[ RMSE = \sqrt{\frac{1}{N} \sum_{i=1}^{N} (y_i - \hat{y}_i)^2} \]
   - Uses `mean_squared_error` with `squared=False` to return RMSE.

---

## Installation and Usage
### **Prerequisites**
Ensure you have the following installed:
- Python 3.x
- Pandas
- NumPy
- Scikit-learn
- SciPy

### **Installation**
```bash
pip install pandas numpy scikit-learn scipy
```



## Contributing
If you’d like to contribute, please fork the repository and use a feature branch. Pull requests are warmly welcome.



