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
<br>
supply=data["Drivers Active Per Hour"]

figure=px.scatter(data, x="Drivers Active Per Hour", y="Riders Active Per Hour", trendline="ols", title="Demand and Supply Analysis")
figure.update_layout(xaxis_title="Number of Drivers Active per Hour (Supply)", yaxis_title="Number of Riders Active per Hour (Demand)",)
figure.show()
![image](https://user-images.githubusercontent.com/95108103/230728734-2bc6e5ad-3890-4e9c-9f63-5edf79a574ab.png)

#so there is a constant relationship between the number of drivers per hour and the number of riders active per hour, it means that for every X  drivers there is a consistent and predictable Y number of riders
<br>
<br>
#Now let's calculate elasticity of demand concerning the number of active drivers per hour
<br>
<br>
avg_demand=data["Riders Active Per Hour"].mean()
<br>
avg_supply=data["Drivers Active Per Hour"].mean()

pct_change_demand=(max(data["Riders Active Per Hour"]) - min(data["Riders Active Per Hour"]))/avg_demand*100
pct_change_supply=(max(data["Drivers Active Per Hour"]) - min(data["Drivers Active Per Hour"]))/avg_supply*100
elasticity=pct_change_demand/pct_change_supply
print("Elasticity of demand with respect to the number of active drivers per hour:{:.2f}".format(elasticity))

![image](https://user-images.githubusercontent.com/95108103/230729070-ecbacadf-5428-4273-9435-b56e31d22094.png)

It signifies a positive relationship between the demand for rides and the number of active drivers per hour.  Specifically it means that a 1% increase in the number of active drivers per hour would lead to a 0.82% decrease in demand for rides.
<br>
<br>
#This level of elasticity suggest that the demand for rides is somewhat senstitive to changes in the number of active drivers per hour
<br>
<br>
#Now let's add a new column in the dataset by calculating the supply ratio:
#calculate the supply ratio for each level of driver activity
data["Supply Ratio"]=data["Rides Completed"]/data["Drivers Active Per Hour"]
print(data.head())

![image](https://user-images.githubusercontent.com/95108103/230731778-8bf673af-faef-4444-98d3-5b224b7bec2a.png)

#Now let's visualize the supply ratio:
<br>
fig=go.Figure()
fig.add_trace(go.Scatter(x=data["Drivers Active Per Hour"], y=data["Supply Ratio"], mode="markers"))

fig.update_layout(
    title="Supply Ratio vs Driver Activity",
    xaxis_title="Driver Activity(Drivers Activity Per Hour)",
    yaxis_title="Spply Ratio (Rides Completed per Driver Active per Hour)")
fig.show()

#The below graph shows the ratio of the number of drivers active per hour and the number of rides completed in an hour. 

![image](https://user-images.githubusercontent.com/95108103/230731875-272b7c97-cbd9-49dc-ae3c-1bb8e560fb69.png)

 This demand supply analysis helps businesses understand the factors influencing consumer demand to maximize profits.  






