
````markdown
# ✈️ Flight Price Prediction using Machine Learning

This project predicts flight ticket prices based on user-provided inputs such as airline, source, destination, departure and arrival times, and other travel details.

## 📁 Project Structure

- `pipe.pkl` – Pre-trained pipeline file (includes preprocessing + ML model)
- `Flight_Price_Prediction.ipynb` – Jupyter Notebook to interact with the model
- `pickel_load.ipynb` – Notebook to test and load model predictions
- `README.md` – This documentation file

---

## 🧠 Model Details

The pipeline (`pipe.pkl`) includes:
- Categorical encoding (Airline, Source, Destination, Additional_Info)
- Time feature processing (e.g., hours, minutes)
- A regression model (e.g., RandomForest or XGBoost) trained to predict price

---

## 🚀 How to Use

### 1. Clone or Download This Repo

```bash
git clone https://github.com/your-repo/flight-price-predictor.git
cd flight-price-predictor
````

### 2. Install Required Libraries

Make sure you have the following Python libraries installed:

```bash
pip install numpy scikit-learn pandas
```

If using Jupyter:

```bash
pip install notebook
```

### 3. Run the Prediction Script

You can run the prediction by executing the following script in a Jupyter Notebook:

```python
import pickle
import numpy as np

# Load the model
pipe = pickle.load(open('pipe.pkl', 'rb'))

# Collect input from user
Airline = input("Enter Airline: ")
Source = input("Enter Source: ")
Destination = input("Enter Destination: ")
Additional_Info = input("Enter Additional Info: ")

Date = int(input("Enter Date (1–31): "))
Month = int(input("Enter Month (1–12): "))
Year = int(input("Enter Year (e.g., 2025): "))

Dep_Hour = int(input("Enter Departure Hour (0–23): "))
Dep_Min = int(input("Enter Departure Minute (0–59): "))

Duration_Hour = int(input("Enter Flight Duration Hour(s): "))
Duration_Min = int(input("Enter Flight Duration Minute(s): "))

Arr_Hour = int(input("Enter Arrival Hour (0–23): "))
Arr_Min = int(input("Enter Arrival Minute (0–59): "))

# Prepare input
test_input = np.array([
    Airline, Source, Destination, Additional_Info,
    Date, Month, Year,
    Dep_Hour, Dep_Min,
    Duration_Hour, Duration_Min,
    Arr_Hour, Arr_Min
], dtype=object).reshape(1, -1)

# Predict
prediction = pipe.predict(test_input)
print("Predicted Flight Price: ₹", round(prediction[0], 2))
```

---

## ✅ Example Input

```
Airline: IndiGo
Source: Delhi
Destination: Cochin
Additional_Info: No info
Date: 25
Month: 5
Year: 2025
Dep_Hour: 10
Dep_Min: 30
Duration_Hour: 2
Duration_Min: 45
Arr_Hour: 13
Arr_Min: 15
```

**Predicted Price:** ₹4583.25 *(Example Output)*

---

## 📌 Notes

* Ensure `pipe.pkl` was trained using the exact same feature order and formats.
* All categorical inputs must match training categories (e.g., use "IndiGo", not "indigo").

---

## 🤝 Contributing

Feel free to fork and improve the model, add UI, or expand the dataset.

---

## 📧 Contact

For issues or questions, email: [yatul247@gmail.com](mailto:yatul247@gmail.com)

---

## 📜 License

MIT License

```

---

Let me know if you want to turn this into a `Streamlit` app or a web form too!
```
