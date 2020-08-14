# python-homework
#Import library
import pandas as pd
from pathlib import Path
%matplotlib inline


#Set file path and read in csv as dataframe
csv_path=Path('../Desktop/budget_data.csv')
budget_data=pd.read_csv(csv_path)
budget_data

#Set the date as the index
budget_data.set_index(budget_data['Date'], inplace=True)
budget_data.head()

#Drop the Date column
budget_data.drop(columns=['Date'], inplace=True)
budget_data

#Use the sum function to get the net amount of profit/losses
budget_total=budget_data.sum(axis=None, skipna=None, level=None, numeric_only=None, min_count=0)
budget_total

#Get the daily percent change
budget_changes=budget_data.diff()
budget_changes.head()

#Add the daily percent changs to get the total amount of changes
budget_returns=budget_changes.mean()
budget_returns

#Get the largest increase in profits
budget_max=budget_changes.max()
budget_max

#Get the greatest decrease in profits
budget_min=budget_changes.min()
budget_min


#Print out results
print('Financial Analysis')
print('---------------------')
print(f"Total Profit/Losses {budget_total}")
print(f'Average Change {budget_returns}')
print(f"Greatest Increase in Profts {budget_max}")
print(f"Greatest Decrease in Profts {budget_min}")
