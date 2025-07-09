# Mock_MatplotLib

1 Problem 1 : https://tinyurl.com/MatplotlibInterviewQuestion
------------------------------------------------
Imagine you are working for a travel agency named "Wanderlust Adventures." Your team has been assigned a project to analyze and visualize the travel data for the past year. The data includes information about various destinations, the number of travelers per month, and the revenue generated. As the data analyst, you decide to use Matplotlib to create insightful visualizations.
As a data analyst at "Wanderlust Adventures," you have been given a dataset containing monthly travel data for different destinations. The dataset includes information about the number of travelers and the revenue generated each month. Your task is to create three visualizations using Matplotlib: a line plot, a pie chart, and a scatter plot.

------------------------------------------------
#1. Line Plot: Monthly trend of Travelers and Revenue

import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("travel.csv")

# Ensure months are in correct chronological order
month_order = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 
               'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
df['Month'] = pd.Categorical(df['Month'], categories=month_order, ordered=True)

# Group data by month and calculate total travelers and revenue
monthly_data = df.groupby('Month').agg({'Travelers': 'sum', 'Revenue': 'sum'}).reindex(month_order)

# Create the line plot
plt.figure(figsize=(10, 6))
plt.plot(monthly_data.index, monthly_data['Travelers'], marker='o', label='Travelers', color='blue')
plt.plot(monthly_data.index, monthly_data['Revenue'], marker='s', label='Revenue', color='green')
plt.title('Monthly Travelers and Revenue Trend')
plt.xlabel('Month')
plt.ylabel('Count / Revenue')
plt.legend()
plt.grid(True)
plt.xticks(rotation=45)
plt.tight_layout()
plt.show()

--------------------------------------------------------

#2. Pie Chart: Top 5 Destinations by Traveler Count

import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("travel.csv")

# Group data by destination and sum the traveler count, then select top 5
destination_data = df.groupby('Destination')['Travelers'].sum().sort_values(ascending=False).head(5)

# Create the pie chart
plt.figure(figsize=(8, 8))
plt.pie(destination_data, labels=destination_data.index, autopct='%1.1f%%', startangle=140)
plt.title('Top 5 Destinations by Traveler Count')
plt.axis('equal')  # Keeps the pie chart circular
plt.tight_layout()
plt.show()

------------------------------------------------------------------------------------

import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("travel.csv")

# Group data by destination and sum the traveler count, then select top 5
destination_data = df.groupby('Destination')['Travelers'].sum().sort_values(ascending=False).head(5)

# Create the pie chart
plt.figure(figsize=(8, 8))
plt.pie(destination_data, labels=destination_data.index, autopct='%1.1f%%', startangle=140)
plt.title('Top 5 Destinations by Traveler Count')
plt.axis('equal')  # Keeps the pie chart circular
plt.tight_layout()
plt.show()

------------------------------------------------------------------------------------
#3. Scatter Plot: Travelers vs Revenue Per Month

import pandas as pd
import matplotlib.pyplot as plt

# Load the dataset
df = pd.read_csv("travel.csv")

# Ensure months are in correct chronological order
month_order = ['Jan', 'Feb', 'Mar', 'Apr', 'May', 'Jun', 
               'Jul', 'Aug', 'Sep', 'Oct', 'Nov', 'Dec']
df['Month'] = pd.Categorical(df['Month'], categories=month_order, ordered=True)

# Group data by month and calculate totals
monthly_data = df.groupby('Month').agg({'Travelers': 'sum', 'Revenue': 'sum'}).reindex(month_order)

# Create the scatter plot
plt.figure(figsize=(10, 6))
plt.scatter(monthly_data['Travelers'], monthly_data['Revenue'], color='orange', edgecolors='black')

# Annotate each point with the month name
for i, month in enumerate(monthly_data.index):
    plt.text(monthly_data['Travelers'][i], monthly_data['Revenue'][i], month)

plt.title('Travelers vs Revenue per Month')
plt.xlabel('Total Travelers')
plt.ylabel('Total Revenue')
plt.grid(True)
plt.tight_layout()
plt.show()






