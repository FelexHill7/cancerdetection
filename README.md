# Breast Cancer Detection Modelling Project

Python, JupyterNotebook, SciKitLearn, TensorFlow, PyTorch, NumPy, Pandas, MatPlotLib, Seaborn

## Project Overview
This project develops machine learning models to classify breast tumors as benign or malignant using a dataset of clinical features. By preprocessing data, training multiple algorithms, and evaluating performance, it demonstrates end-to-end ML pipeline skills for real-world healthcare applications.

## Dataset Description
The dataset contains clinical measurements from breast cancer biopsies, including features like radius, texture, perimeter, and area. Preprocessing involved handling categorical variables, performing an 80/20 train-test split, and applying standardization to ensure model compatibility and reduce bias from outliers.

## Installation
1. Clone the repository: `git clone <repo-url>`
2. Install dependencies: `pip install -r requirements.txt`
3. Run notebooks in Jupyter: `jupyter notebook`

## Usage
- Preprocess data: Run `notebooks/data_preprocessor.ipynb`
- Train models: Execute `notebooks/logistic_regression.ipynb`, `notebooks/svm_classifier.ipynb`, or `notebooks/neural_network.ipynb`
- Compare results: Use `notebooks/model_comparison.ipynb`
- View predictions: Check `models/` folder for CSV outputs

## Results
- **Accuracy**: All models > 96% accurate
- **F1-Score**: All models > 0.95
- Visualizations: Decision boundaries and PCA plots in notebooks

## Successes
- Trained and modeled supervised learning algorithms (Support Vector Machine, Logistic Regression and Neural Network) to classify breast tumors as benign or malignant in Python.
- Preprocessed dataset using pandas by performing One-Hot-Encoding and turning categorical string values into numerical features, performing an 80/20 train–test split, and applying feature scaling with standardization to increase accuracy and prevent any outliers from dominating bias and weight.
- Achieved above 96% accuracy across all models through model-specific fine-tuning and algorithms such as the ReLU activation function and the Radial Basis Function kernel through SciKitLearn.
- Visualized model predictions using Matplotlib and dimensionality reduction techniques (Principal Component Analysis) to analyze training loss per epoch, decision boundaries, and 2D/3D feature distributions.
- Designed the scripts to output prediction results, optimal training parameters and f1 scores for model comparisons.

## Model Architecture and Hyperparameters
- **Neural Network**: 3-layer architecture with ReLU activation, trained for 100 epochs using Adam optimizer.
- **SVM**: RBF kernel with C=1.0, gamma='scale'.
- **Logistic Regression**: L2 regularization with C=1.0.

## Key Features
- Automated hyperparameter tuning using GridSearchCV.
- Interpretable models for clinical decision-making.
- Comprehensive model comparison with F1-scores and predictions.

## Challenges
- Dealing with raw data. Preprocessed data through learning scaling and standard deviation formula to apply to all features through Pandas
- Selecting model functions. Picked Sigmoid activation function over ReLU due to stability, natural mapping of probability and continuity for gradient descent. Picked Kernel Radial Basis due to non-linear data—allowing for complex, smooth decision boundaries, efficiency and higher-dimensional mapping,
- Tuning hyperparameters. Overcome by researching what high and low values do based on dataset sizing and playing around with values.

## Future Work
- Explore ensemble methods (e.g., Random Forest).
- Deploy as a web app with Flask.
- Integrate with larger healthcare datasets for improved generalization.

## Contributing
Contributions welcome! Please open an issue for bugs or feature requests.

## License
Licensed under MIT.
