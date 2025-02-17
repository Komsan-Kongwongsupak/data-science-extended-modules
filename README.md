# Data Science Assistant and scikit-learn Extensions

This repository contains two main components:

1. **`assistant.py`**: A data science assistant script for managing and analyzing datasets in data science projects.
2. **`sklearnext`**: A library to extend the functionalities of `scikit-learn`, providing custom transformers and data balancers.

---

## Repository Structure

```
.
├── assistant.py          # A utility script for managing data in data science projects
└── sklearnext            # A directory containing custom scikit-learn extensions
    ├── balancing.py      # Custom class for balancing binary classification datasets
    └── preprocessing.py  # Custom transformer for label encoding
```

---

## `assistant.py`

This script provides utilities for dataset analysis and splitting, with features such as:
- **DataFrame Reports**: Automatically generates detailed reports for both numerical and categorical columns, including outlier detection and distribution analysis.
- **Data Splitting**: Functions to split datasets into training and testing sets, with options for exporting and importing the splits as CSV files.
- **Data Type Casting**: A helper function to convert strings to appropriate data types.

### Example Usage
```python
from assistant import report, split_and_export

# Create a report for a DataFrame
df_report = report(df)
df_report.show()
df_report.export()

# Split and export data
split_and_export(df, target="target_column", test_ratio=0.2, path="./data")
```

---

## `sklearnext`

A library to extend `scikit-learn` with custom transformers and data balancers.

### `balancing.py`

Defines `BinaryDataBalancer`, a custom class for balancing binary classification data using:
- **SMOTE** for oversampling
- **Random resampling** for downsampling

This transformer ensures the dataset meets a specified positive-to-negative class ratio.

### Example Usage
```python
from sklearnext.balancing import BinaryDataBalancer

# Balance the dataset with a 1:1 positive-to-negative ratio
balancer = BinaryDataBalancer(ratio=1.0)
X_balanced, y_balanced = balancer.fit_transform(X, y)
```

---

### `preprocessing.py`

Defines `LabelEncoderTransformer`, a custom transformer that uses `LabelEncoder` for converting categorical features to numerical labels.

### Example Usage
```python
from sklearnext.preprocessing import LabelEncoderTransformer
from sklearn.compose import ColumnTransformer

# Apply label encoding to a categorical column
label_encoder = LabelEncoderTransformer()
encoded_column = label_encoder.fit_transform(categorical_column)
```

---

## Installation

To use the utilities in this repository, ensure the following dependencies are installed:
- `pandas`
- `numpy`
- `scipy`
- `scikit-learn`
- `imbalanced-learn`

Install them via pip:
```bash
pip install pandas numpy scipy scikit-learn imbalanced-learn
```

---

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
```

Let me know if you'd like any adjustments!
