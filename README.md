# baseball
just to find out the potential of the player
# Standard data analysis imports with quandl used for financial data
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
from matplotlib import style
import quandl
import seaborn as sns
import math
# These are the DataFrames containing the raw data as provided by Sean Lahman
all_salaries = pd.read_csv('Salaries.csv')
all_batting = pd.read_csv('Batting.csv')
all_pitching = pd.read_csv('Pitching.csv')

# Set up pylab to run in the Jupyter Notebook
%pylab inline
# Group the salaries by mean 
yearly_average_salary = all_salaries.groupby('yearID').mean()
# Calculate and plot the percentage change from the first entry
yearly_salary_pct_change = 100.0 *  (yearly_average_salary - yearly_average_salary.iloc[0]) / yearly_average_salary.iloc[0]
yearly_salary_pct_change.plot()
plt.title('Average MLB Player Slayer')
plt.ylabel('PCT Change'); plt.xlabel('')
# Retrieve data from Quandl with the start date that corresponds to the MLB salary start date
median_household_income = quandl.get('FRED/MEHOINUSA646N', start_date = '1985-01-01')
# Calculate and plot the percentage change of median household income from the first entry
median_household_pct_change = 100.0 * (median_household_income - median_household_income.iloc[0]) / median_household_income.iloc[0]
median_household_pct_change.plot(color = 'c')
plt.title('Median US Household Income')
plt.ylabel('PCT Change'), plt.xlabel('');
