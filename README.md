# fishycptfront
 🐟  🐟  🐟  🐟  🐟  🐟  🐟 
 
# Frontend for Medical Prediction Models

Welcome to the frontend repository for our medical prediction models. This project provides a user-friendly interface for three machine learning models: stroke detection, heart attack prediction, and Titanic survival prediction. The models are designed to assist in early detection and prediction, potentially saving lives through timely interventions.

## Table of Contents
- [Overview](#overview)
- [Features](#features)
- [Installation](#installation)
- [Usage](#usage)
- [Model Details](#model-details)
- [Contributing](#contributing)
- [License](#license)

## Overview

This frontend application provides a simple and intuitive interface for interacting with three different machine learning models:
1. **Stroke Detection**: Predicts the likelihood of a stroke based on user input data.
2. **Heart Attack Prediction**: Estimates the risk of a heart attack using relevant health metrics.
3. **Titanic Survival Prediction**: Predicts the chances of survival on the Titanic given certain passenger details.

## Features

- **User-Friendly Interface**: Easy-to-navigate forms to input data for each prediction model.
- **Real-time Predictions**: Instantly get predictions after submitting the input data.
- **Detailed Results**: View comprehensive prediction results and relevant risk factors.

## Installation

### Prerequisites

- Node.js (v14.0.0 or higher)
- npm (v6.0.0 or higher)

### Steps

1. **Clone the Repository**:
    ```sh
    git clone https://github.com/yourusername/medical-prediction-frontend.git
    cd medical-prediction-frontend
    ```

2. **Install Dependencies**:
    ```sh
    npm install
    ```

3. **Start the Development Server**:
    ```sh
    npm start
    ```

The application should now be running on `http://localhost:3000`.

## Usage

1. **Stroke Detection**:
    - Navigate to the Stroke Detection section.
    - Fill in the required health data such as age, hypertension, heart disease, etc.
    - Click on the 'Predict' button to get the prediction.

2. **Heart Attack Prediction**:
    - Go to the Heart Attack Prediction section.
    - Input the necessary health metrics like cholesterol levels, resting blood pressure, etc.
    - Submit the form to receive the prediction.

3. **Titanic Survival Prediction**:
    - Access the Titanic Prediction page.
    - Enter passenger details like age, gender, class, etc.
    - Click on 'Predict' to see the survival prediction.

## Model Details

### Stroke Detection Model

- **Input Features**: Age, Hypertension, Heart Disease, Ever Married, Work Type, Residence Type, Average Glucose Level, BMI, Smoking Status.
- **Algorithm**: Logistic Regression / Random Forest / Other (Specify the algorithm used).

### Heart Attack Prediction Model

- **Input Features**: Age, Sex, Chest Pain Type, Resting Blood Pressure, Cholesterol, Fasting Blood Sugar, Resting ECG, Maximum Heart Rate Achieved, Exercise Induced Angina, ST Depression.
- **Algorithm**: Support Vector Machine / Decision Tree / Other (Specify the algorithm used).

### Titanic Survival Prediction Model

- **Input Features**: Age, Gender, Passenger Class, Siblings/Spouses Aboard, Parents/Children Aboard, Fare.
- **Algorithm**: Decision Tree / K-Nearest Neighbors / Other (Specify the algorithm used).

## Contributing

We welcome contributions to improve the project. To contribute, follow these steps:

1. Fork the repository.
2. Create a new branch (`git checkout -b feature-branch`).
3. Make your changes and commit them (`git commit -m 'Add some feature'`).
4. Push to the branch (`git push origin feature-branch`).
5. Create a new Pull Request.

Please ensure your code follows our coding conventions and is well-documented.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.

---

Feel free to open issues or contact us if you have any questions or need further assistance. Happy coding!
