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

