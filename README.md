Demand and Supply Analysis is a valuable concept used to see the relatioship between the quantity demanded and the quantity supplied.  Demand and Supply analysis means analyzing the relationship between the quantity demanded and the quantity supplied.  This helps businesses understand the factors influencing consumer demand to maximize profits.
<br>
<br>
The data set riders.csv has information on demand for cab rides at a given time, the availability at a given time and the rides completed at a given time.
<br>
<br>
import necessary pythn libraries and the dataset
<br>
import pandas as pd
import plotly.express as px
import plotly.graph_objects as go
import plotly.io as pio
pio.templates.default="plotly_white"

data=pd.read_csv('rides.csv')
print(data.head())

![image](https://user-images.githubusercontent.com/95108103/230728379-a07b7631-31ea-4b2f-87b5-9a535bfe8a54.png)

#lets have a look if the dataset has null values or not

print(data.isnull().sum())

![image](https://user-images.githubusercontent.com/95108103/230728658-eda513c4-e9fb-4d7a-9fb5-70836e14e3b7.png)


#the dataset has 54 values in Rides Completed column.  I'll drop these to move forward

data=data.dropna()

#Now lets analyze the relationship between the number of drivers active per hour and the number of riders activer per hour 
<br>
demand=data["Riders Active Per Hour"]
supply=data["Drivers Active Per Hour"]

figure=px.scatter(data, x="Drivers Active Per Hour", y="Riders Active Per Hour", trendline="ols", title="Demand and Supply Analysis")
figure.update_layout(xaxis_title="Number of Drivers Active per Hour (Supply)", yaxis_title="Number of Riders Active per Hour (Demand)",)
figure.show()
![image](https://user-images.githubusercontent.com/95108103/230728734-2bc6e5ad-3890-4e9c-9f63-5edf79a574ab.png)

