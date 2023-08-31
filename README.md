# yieldspreadLSTM
This repository contains a framework for training and evaluating long short-term memory (LSTM) models for yield spread forecasting. The user can open and run the notebook in Google Colaboratory or download the notebook and run it locally. 

The LSTM learns to predict labels (yield spreads) from sequences of training data (in this case, a sequence of the last 20 days of yield spreads and market data). The model takes advantage of the time-series nature of the data, achieving good generalization to the validation/test sets.

The user provides a CSV with daily market data and yields for the assets of interest. The user must specify the names of the assets as strings in the variable asset_names. From here, the the columns of the CSV corresponding to yields are automatically separated from those corresponding to market data. Columns containing the yield spreads between each asset are calculated and used as training/validation/test labels. Entries containing NaN values are filled with the last numerical value recorded in that column. If a column starts with NaN values, those missing entries are filled with zeros.  

The data is then processed into 20-day sequences. For example, a training example would contain yield spreads and market info from June 1st through June 20th, and its corresponding label would be a vector containing the yield spreads between all assets of interest on June 21st.

When training the model, it is possible to specify different prediction horizons by changing the horizon variable. In the notebook, the horizon variable is set to 0, which corresponds to a one day horizon. It can also be set to 6, 13, or 20, to train models for a one, two, or three week prediction horizon. 

