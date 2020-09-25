#! Creating a Neural Network in Keras

<img src="https://miro.medium.com/max/874/1*eJ36Jpf-DE9q5nKk67xT0Q.jpeg">

In this project I'm going to build a neural network.


** 1. Preprocess data (`preprocess_data.py`)**

1. Read the file `sales_data_training.csv` and `sales_data_test.csv` with pandas using `pd.read_csv(filename)`
2. Data needs to be scaled to a small range like 0 to 1 for the neural, you can do it with the method `MinMaxScaler` of `scikit learn`

    ```python
    from sklearn.preprocessing import MinMaxScaler
    scaler =  MinMaxScaler(feature_range=(0, 1))
    ```

3. Use `scaler.fit_transform` and `scaler.transform` to scale the training inputs and outputs

    ```python
    scaled_training = scaler.fit_transform(training_data_df)
    scaled_testing = scaler.transform(test_data_df)
    ```

4. Create new pandas DataFrame objects from the scaled data

    ```python
    scaled_training_df = pd.DataFrame(scaled_training, columns=training_data_df.columns.values)
    scaled_testing_df = pd.DataFrame(scaled_testing, columns=test_data_df.columns.values)
    ```

5. Save scaled data dataframes to new CSV files

```python
scaled_training_df.to_csv("sales_data_training_scaled.csv", index=False)
scaled_testing_df.to_csv("sales_data_testing_scaled.csv", index=False)
```