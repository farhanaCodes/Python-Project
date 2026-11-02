
# 🍔 Food Delivery Time Predictor

![Python](https://img.shields.io/badge/Python-3.9%2B-blue?logo=python&logoColor=white)
![Machine Learning](https://img.shields.io/badge/Machine%20Learning-Scikit--Learn-orange?logo=scikitlearn&logoColor=white)
![Streamlit](https://img.shields.io/badge/Streamlit-Web%20App-red?logo=streamlit&logoColor=white)
![Status](https://img.shields.io/badge/Project-Completed-success)

A complete end-to-end Machine Learning project built with **Python, Scikit-Learn, and Streamlit** to estimate food delivery durations based on real-world operational factors such as route distance, kitchen preparation time, traffic conditions, weather severity, and rider experience.

---

## 📌 Project Overview

Accurate delivery time estimation is important for customer satisfaction and efficient food delivery operations.

This project demonstrates the complete data science lifecycle, from synthetic data generation to model training and interactive deployment.

### Key Features

- **Synthetic Data Generation:** Generates 1,500 delivery records using realistic operational formulas.
- **Exploratory Data Analysis (EDA):** Examines feature distributions, missing values, data types, and correlations.
- **Machine Learning:** Trains a Multiple Linear Regression model to estimate delivery time.
- **Model Evaluation:** Evaluates predictions using MAE, MSE, RMSE, and R² score.
- **CLI Prediction:** Provides an interactive command-line interface for individual predictions.
- **Interactive Web Dashboard:** Offers a dark-themed Streamlit application for real-time delivery time estimation.

---

## 🔄 End-to-End Project Workflow

```text
       01_create_data.py
               |
               v
       delivery_data.csv
               |
       +-------+-------+
       |               |
       v               v
02_explore_data.py  03_train_model.py
   (EDA)             (Model Training)
                           |
                           v
                   delivery_model.pkl
                           |
                   +-------+-------+
                   |               |
                   v               v
             04_predict.py     05_app.py
                (CLI)        (Streamlit App)
```

### Detailed Pipeline Breakdown

#### 1. Data Generation — `01_create_data.py`

- Generates 1,500 synthetic food delivery records.
- Uses controlled random distributions to simulate delivery conditions.
- Saves the generated dataset as `delivery_data.csv`.

#### 2. Data Exploration — `02_explore_data.py`

- Checks missing values and data types.
- Analyzes relationships between input features and delivery time.
- Generates scatter plots and correlation insights.

#### 3. Model Training — `03_train_model.py`

- Splits the dataset into 80% training and 20% testing data.
- Uses `random_state=42` for reproducibility.
- Trains a Scikit-Learn `LinearRegression` model.
- Evaluates model performance using MAE, MSE, RMSE, and R².
- Saves the trained model and feature mappings to `delivery_model.pkl`.

#### 4. CLI Prediction — `04_predict.py`

- Accepts delivery details through the terminal.
- Predicts the estimated delivery duration for an individual order.

#### 5. Web Application — `05_app.py`

- Provides an interactive Streamlit dashboard.
- Allows users to adjust delivery parameters.
- Displays estimated delivery time and an order summary.

---

## 📁 Repository Structure

```text
food-delivery-time-predictor/
│
├── 01_create_data.py       # Generates the synthetic dataset
├── 02_explore_data.py      # Performs EDA and visualizations
├── 03_train_model.py       # Trains and evaluates the ML model
├── 04_predict.py           # CLI prediction interface
├── 05_app.py               # Streamlit web application
│
├── delivery_data.csv       # Dataset containing 1,500 records
├── delivery_model.pkl      # Serialized trained model
├── README.md               # Project documentation
└── LICENSE                 # Project license, if included
```

---

## 📊 Dataset and Features

The model uses five operational features to estimate the target variable, `delivery_time_min`.

| Feature | Type | Unit / Range | Description |
|---|---|---|---|
| `distance_km` | Float | 1–15 km | Distance between restaurant and customer |
| `preparation_time_min` | Integer | 5–30 minutes | Time required to prepare the order |
| `traffic_level` | Integer | 1–4 | Traffic intensity: low to severe |
| `weather_severity` | Integer | 0–3 | Weather conditions from clear to severe |
| `rider_experience_years` | Integer | 0–10 years | Delivery rider's experience |
| `delivery_time_min` | Float | Minutes | Target variable: total delivery time |

**Note:** The dataset is synthetically generated for educational and demonstration purposes. It does not represent verified real-world delivery records.

---

## 📈 Model Performance and Results

The dataset contains 1,500 records and is divided into training and testing sets.

| Dataset | Number of Records |
|---|---:|
| Training Set (80%) | 1,200 |
| Testing Set (20%) | 300 |
| Total | 1,500 |

### Evaluation Metrics

| Metric | Score |
|---|---:|
| MAE (Mean Absolute Error) | 2.51 minutes |
| MSE (Mean Squared Error) | 9.63 |
| RMSE (Root Mean Squared Error) | 3.10 minutes |
| R² Score | 0.9649 |

The reported R² score indicates that the model explains approximately **96.49% of the variance** in the test-set delivery times.

*These metrics are the reported project results and should be verified by running the training script.*

### Linear Regression Formula

The estimated delivery time is calculated using the following regression equation:

$$
\begin{aligned}
\text{Delivery Time} \approx {} & 4.941 \\
&+ 3.007(\text{distance}) \\
&+ 0.997(\text{prep\_time}) \\
&+ 3.980(\text{traffic}) \\
&+ 1.979(\text{weather}) \\
&- 0.358(\text{rider\_exp})
\end{aligned}
$$

The coefficients represent the estimated contribution of each feature while holding the other features constant.

---

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:

- Python 3.9 or later
- pip (Python package installer)
- Git

### 1. Clone the Repository

Replace `your-username` with your GitHub username.

```bash
git clone https://github.com/your-username/food-delivery-time-predictor.git
cd food-delivery-time-predictor
```

### 2. Install Dependencies

```bash
pip install pandas numpy scikit-learn matplotlib streamlit
```

### 3. Generate the Dataset

```bash
python 01_create_data.py
```

This creates the `delivery_data.csv` file.

### 4. Explore the Dataset

```bash
python 02_explore_data.py
```

This performs exploratory analysis and generates visualizations.

### 5. Train the Machine Learning Model

```bash
python 03_train_model.py
```

This trains the Linear Regression model, evaluates its performance, and saves the model artifact.

### 6. Run CLI Predictions

```bash
python 04_predict.py
```

Follow the prompts in the terminal to enter delivery details and receive an estimated delivery time.

---

## 🌐 Running the Streamlit Web Application

Launch the interactive dashboard using:

```bash
streamlit run 05_app.py
```

The application will usually open automatically in your browser.

If it does not, visit:

[http://localhost:8501](http://localhost:8501)

### Web Application Features

- Responsive three-column layout optimized for desktop screens.
- Dark-themed interface with a purple accent color.
- Interactive sliders and number inputs for delivery parameters.
- Real-time delivery time estimation.
- Order summary card displaying the selected delivery conditions.

---

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Python | Core programming language |
| Pandas | Data manipulation and analysis |
| NumPy | Numerical computation and random data generation |
| Scikit-Learn | Model training, data splitting, and evaluation |
| Matplotlib | Data visualization |
| Streamlit | Interactive web dashboard |
| Git & GitHub | Version control and project hosting |

---

## 🎯 Learning Outcomes

Through this project, I explored:

- End-to-end Machine Learning project development.
- Synthetic dataset creation and preprocessing.
- Exploratory Data Analysis and feature correlation.
- Multiple Linear Regression.
- Model evaluation using regression metrics.
- Model serialization and reuse.
- Building interactive applications with Streamlit.
- Deploying a machine learning workflow through a user-friendly interface.

---

## 🔮 Future Improvements

- Train and compare additional regression models, such as Random Forest and Gradient Boosting.
- Add more realistic features, including restaurant workload and order size.
- Improve model performance through hyperparameter tuning and cross-validation.
- Deploy the Streamlit application online.
- Integrate real-world delivery data when available.

---

## 📝 License

This project is intended for educational and demonstration purposes.

If you choose the MIT License, include a `LICENSE` file containing the appropriate MIT license text. The repository is not automatically MIT-licensed just because this README mentions it.

---

## 👩‍💻 Author

**Your Name**

- GitHub: [your-username](https://github.com/your-username)

Feel free to explore the repository, share feedback, and suggest improvements!
