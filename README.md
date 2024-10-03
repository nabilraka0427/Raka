# Exploratory Data Analysis on Pizza Sales Dataset

**Course**: Infrastruktur dan Platform Sains Data  
**Pertemuan**: 2  
**Topic**: Exploratory Data Analysis (EDA)

This project focuses on conducting **Exploratory Data Analysis (EDA)** on a pizza sales dataset as part of the second session of the course *Infrastruktur dan Platform Sains Data*. The goal of the exploration is to understand the dataset better by cleaning, analyzing, and visualizing the data.

## Project Objectives
The main objective of this project is to explore the dataset through various EDA techniques, allowing us to gain insights and understand the underlying data. The following key points are addressed:

### 1. Load Data
The dataset, which contains pizza sales information, is loaded into the environment. The dataset includes details such as:
- Pizza types
- Order quantities
- Pricing
- Ingredients
- Order dates and times

### 2. Basic Information about the Dataset
In this step, we obtain basic information such as:
- The number of rows and columns in the dataset.
- Column names, data types, and a preview of the data.
- Overview of missing values, if any.

### 3. Checking Duplicate and Unique Values
- **Duplicate Values**: The dataset is checked for duplicate entries.
- **Unique Values**: The dataset is inspected to find the number of unique values for specific columns, such as pizza types, categories, and sizes.

### 4. Visualizing Unique Values
A visualization (e.g., bar chart) is created to show the distribution of unique values for specific categorical features like:
- `pizza_category`
- `pizza_size`
- `pizza_ingredients`

### 5. Finding Null Values
The dataset is analyzed to detect any `null` or missing values. These null values can potentially affect the analysis, so it is important to identify them early.

### 6. Replacing Null Values
All null or missing values are handled and replaced based on the context of the data:
- For numerical columns, mean or median imputation may be used.
- For categorical columns, mode or other methods are considered.

### 7. Understanding Data Types
We inspect the data types of each column to ensure that they are appropriate for further analysis. Knowing the data types helps to determine how to handle the data:
- `int64` for integers (e.g., quantities).
- `float64` for prices.
- `object` for categorical variables (e.g., pizza names, ingredients).

### 8. Data Filtering
The dataset is filtered based on specific criteria to focus on certain data points. For example:
- Orders within a certain date range.
- Specific pizza categories (e.g., only "Veggie" pizzas).

### 9. Box Plot Creation
A **box plot** is created to visualize the distribution and spread of numerical features, such as:
- `unit_price` and `total_price`: This helps to detect outliers and understand the pricing distribution across pizza types.

### 10. Correlation Analysis
The correlation between numerical features (e.g., `quantity`, `unit_price`, `total_price`) is calculated to see how they are related. This step helps in identifying potential relationships between variables that may be useful for further modeling or analysis.

---

## Example of the Dataset
Here's a preview of the dataset being explored:

| pizza_id | order_id | pizza_name_id | quantity | order_date | order_time | unit_price | total_price | pizza_size | pizza_category | pizza_ingredients | pizza_name              |
|----------|----------|---------------|----------|------------|------------|------------|-------------|------------|----------------|-------------------|-------------------------|
| 1.0      | 1.0      | hawaiian_m    | 1.0      | 1/1/2015   | 11:38:36   | 13.25      | 13.25       | M          | Classic        | Sliced Ham, Pineapple, Mozzarella Cheese | The Hawaiian Pizza     |
| 2.0      | 2.0      | classic_dlx_m | 1.0      | 1/1/2015   | 11:57:40   | 16.00      | 16.00       | M          | Classic        | Pepperoni, Mushrooms, Red Onions, Red Peppers,... | The Classic Deluxe Pizza |
| 3.0      | 2.0      | five_cheese_l | 1.0      | 1/1/2015   | 11:57:40   | 18.50      | 18.50       | L          | Veggie         | Mozzarella Cheese, Provolone Cheese, Smoked Go... | The Five Cheese Pizza  |

---

## Getting Started

### Prerequisites
- Python 3.x
- Libraries: `pandas`, `numpy`, `matplotlib`, `seaborn`

### Installation
1. Clone this repository
   ```bash
   git clone https://github.com/username/pizza-eda.git
pip install -r requirements.txt

### 2. Example Dataset (`pizza_sales.csv`)

Save the following as `pizza_sales.csv` and include it in the repository:
License
```csv
pizza_id,order_id,pizza_name_id,quantity,order_date,order_time,unit_price,total_price,pizza_size,pizza_category,pizza_ingredients,pizza_name
1.0,1.0,hawaiian_m,1.0,1/1/2015,11:38:36,13.25,13.25,M,Classic,Sliced Ham, Pineapple, Mozzarella Cheese,The Hawaiian Pizza
2.0,2.0,classic_dlx_m,1.0,1/1/2015,11:57:40,16.00,16.00,M,Classic,Pepperoni, Mushrooms, Red Onions, Red Peppers,The Classic Deluxe Pizza
3.0,2.0,five_cheese_l,1.0,1/1/2015,11:57:40,18.50,18.50,L,Veggie,Mozzarella Cheese, Provolone Cheese, Smoked Gouda, Parmesan Cheese,The Five Cheese Pizza
4.0,2.0,ital_supr_l,1.0,1/1/2015,11:57:40,20.75,20.75,L,Supreme,Calabrese Salami, Capocollo, Tomatoes, Red Onions,The Italian Supreme Pizza
5.0,2.0,mexicana_m,1.0,1/1/2015,11:57:40,16.00,16.00,M,Veggie,Tomatoes, Red Peppers, Jalapeno Peppers, Red Onions,The Mexicana Pizza

pandas
numpy
matplotlib
seaborn

├── README.md
├── pizza_sales.csv
└── requirements.txt

