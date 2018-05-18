
# Possible Trends


Summary: 
Upon completion of reviewing the data - the following things needed to be reviewed:
    
Mystery dot: 

Port James is the mystery outlier dot in the Suburban area. The data shows that Port James Suburbia has a ride count of 64, which is significantly higher than the other Suburban categories for each city. So the debate began, prior to removing a dot for data error - it must actually be confirmed it’s an error. Since being limited in going to the source of the data - it can not be eliminated. It also begs the questions, if it isn’t a data error - what is Port James doing that is so amazing ? Does this # represent a possible trend that could occur in Suburbia? Is Port James being progressive in their ways and realizing less cars and more Uber is better? Do the Suburbs of Port James have leadership that are doing things to incentivize the public to uber more? OR… is it just a data entry error? 
Also, upon conferring with a few colleagues - who also were troubled by the mystery dot - they created their plots slightly different - Being honest, I don’t want to take credit for their ideas - but I’d like to address it. The alternate way of combining the data appears to have allowed the Port James data to be merged properly and not be summed up to a 64 ride count - however, the dot was still there… it doesn’t appear to be an outlier - and it just looked like an additional suburbia dot… But because of knowing the extreme that showed up the opposed way of combining the data - I can see the dot and it still shows a higher/greater count of something going on. Regardless of the location of the dot the data can’t be dropped. 
Because both ways of merging and creating the bubble plots yielded the evidence that Port James has something unique going on - it can’t not be ignored - I think a trip to Port James Suburbia is a warranted proposal! ;-)
    
Spread of Rural areas: 

The Bubble graph appears to show that the fares are higher - hence the high spread of the rural Average Fares. There are some Cities with Rural area that are bringing in some serious fares. This aligns with the fact that rural areas require further driving distance so a higher fare. It does appear you could make some decent extra money on fares in the rural areas, but clearly a lot less rides are received. 

Comparisons of Pie Charts:

Each of the pie charts were divided by Rural, Suburban, and Urban based off of Total Fares, Total Rides and Total Drivers. They all had a decent spread and were divided up relatively evenly for the Total Fares and Rides, but the Total Drivers showed a larger saturation of drivers in the Urban areas compared to the other 2. It does appear that in order for the Suburban and Rural areas to have the #’s that they have, their drivers are busier. 




```python
from matplotlib import pyplot as plt
import pandas as pd
import numpy as np
import seaborn as sns
```


```python
file1_csv = "city_data.csv"
file2_csv = "ride_data.csv"
city_data_df = pd.read_csv(file1_csv)
ride_data_df = pd.read_csv(file2_csv)
```


```python
city_data_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>driver_count</th>
      <th>type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Kelseyland</td>
      <td>63</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Nguyenbury</td>
      <td>8</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>2</th>
      <td>East Douglas</td>
      <td>12</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>3</th>
      <td>West Dawnfurt</td>
      <td>34</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Rodriguezburgh</td>
      <td>52</td>
      <td>Urban</td>
    </tr>
  </tbody>
</table>
</div>




```python
ride_data_df.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sarabury</td>
      <td>2016-01-16 13:49:27</td>
      <td>38.35</td>
      <td>5403689035038</td>
    </tr>
    <tr>
      <th>1</th>
      <td>South Roy</td>
      <td>2016-01-02 18:42:34</td>
      <td>17.49</td>
      <td>4036272335942</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Wiseborough</td>
      <td>2016-01-21 17:35:29</td>
      <td>44.18</td>
      <td>3645042422587</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spencertown</td>
      <td>2016-07-31 14:53:22</td>
      <td>6.87</td>
      <td>2242596575892</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nguyenbury</td>
      <td>2016-07-09 04:42:44</td>
      <td>6.28</td>
      <td>1543057793673</td>
    </tr>
  </tbody>
</table>
</div>




```python
All_Data = pd.merge(ride_data_df,city_data_df, how ="left", on=['city'])
All_Data.head()
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead th {
        text-align: right;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>city</th>
      <th>date</th>
      <th>fare</th>
      <th>ride_id</th>
      <th>driver_count</th>
      <th>type</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>Sarabury</td>
      <td>2016-01-16 13:49:27</td>
      <td>38.35</td>
      <td>5403689035038</td>
      <td>46</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>1</th>
      <td>South Roy</td>
      <td>2016-01-02 18:42:34</td>
      <td>17.49</td>
      <td>4036272335942</td>
      <td>35</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>2</th>
      <td>Wiseborough</td>
      <td>2016-01-21 17:35:29</td>
      <td>44.18</td>
      <td>3645042422587</td>
      <td>55</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>3</th>
      <td>Spencertown</td>
      <td>2016-07-31 14:53:22</td>
      <td>6.87</td>
      <td>2242596575892</td>
      <td>68</td>
      <td>Urban</td>
    </tr>
    <tr>
      <th>4</th>
      <td>Nguyenbury</td>
      <td>2016-07-09 04:42:44</td>
      <td>6.28</td>
      <td>1543057793673</td>
      <td>8</td>
      <td>Urban</td>
    </tr>
  </tbody>
</table>
</div>




```python
Avg_fare_city = All_Data.groupby("city")['fare'].mean()
Total_ride_city = All_Data.groupby("city")['ride_id'].count()
drive_count_city = All_Data.groupby('city')['driver_count'].max()
city_type_city = All_Data.groupby('city')["type"].max()
Total_fare_city = All_Data.groupby("city")['fare'].sum()
```


```python
Pyber_Bubble_Plot = pd.DataFrame({"Average_Fare": Avg_fare_city,"Total_Rides":Total_ride_city,
                                  "Driver_Count":drive_count_city,"Type":city_type_city,
                                  "Total_Fare":Total_fare_city})
Pyber_Bubble_Plot_Type = Pyber_Bubble_Plot.groupby("Type").sum()

```


```python
Pyber_Bubble_Plot_Type['Total_Rides']
```




    Type
    Rural        125
    Suburban     657
    Urban       1625
    Name: Total_Rides, dtype: int64




```python
Pyber_Bubble_Plot_Type['Driver_Count']
```




    Type
    Rural        104
    Suburban     635
    Urban       2607
    Name: Driver_Count, dtype: int64




```python
Pyber_Bubble_Plot_Fare = Pyber_Bubble_Plot.groupby('Type').sum()
Pyber_Bubble_Plot_Fare['Total_Fare']
```




    Type
    Rural        4255.09
    Suburban    20335.69
    Urban       40078.34
    Name: Total_Fare, dtype: float64




```python
Urban = Pyber_Bubble_Plot[Pyber_Bubble_Plot["Type"] == "Urban"]
Urban_Fare = Urban["Average_Fare"]
Urban_Rides = Urban["Total_Rides"]
Rural = Pyber_Bubble_Plot[Pyber_Bubble_Plot["Type"] == "Rural"]
Rural_Fare = Rural["Average_Fare"]
Rural_Rides = Rural["Total_Rides"]
Suburban = Pyber_Bubble_Plot[Pyber_Bubble_Plot["Type"] == "Suburban"]
Suburb_Fare = Suburban["Average_Fare"]
Suburb_Rides = Suburban["Total_Rides"]

Suburb_Rides.head()

```




    city
    Anitamouth       9
    Campbellport    15
    Carrollbury     10
    Clarkstad       12
    Conwaymouth     11
    Name: Total_Rides, dtype: int64



# Bubble Plot of Ride Sharing Data


```python
x_urban = Urban_Rides
y_urban = Urban_Fare
x_rural = Rural_Rides
y_rural = Rural_Fare
x_suburb = Suburb_Rides
y_suburb = Suburb_Fare

plt.ylim(15, 55)
plt.xlim(-5, 65)
# Add labels to the x and y axes
plt.title("Pyber")
plt.xlabel("Number of Rides")
plt.ylabel("Average Fare ($)")
plt.grid()


urban = plt.scatter(x_urban, y_urban, marker="o", linewidth=1.5,facecolors="lightcoral", edgecolors="black", s=drive_count_city*5,
                    alpha=.7, label = "Urban")
suburb = plt.scatter(x_suburb, y_suburb, marker="o", linewidth=1.5,facecolors="lightskyblue", edgecolors="black",s=drive_count_city*5,
                    alpha=.7, label = "Suburban")
rural = plt.scatter(x_rural, y_rural, marker="o", linewidth=1.5, facecolors="gold", edgecolors="black",s=drive_count_city*5,
                    alpha=.7, label = "Rural")

plt.legend(handles=[urban,suburb,rural], loc="best")

plt.text(66,40, 'Note: Circle size correlates with driver count per city')
plt.savefig("BubblePlot_ShareRidingData.png")

```


![png](output_14_0.png)



```python
#hunt for the outlier... found in Port James
Suburb_Rides["Port James"]
```




    64




```python
#Extra/Optional Code for Seaborn that were in the instructions and then removed from instructions.
#Seaborn looks like a great library to get to use - but the instructor indicated best to not use, so stopped creating 
#sns.lmplot(x="Total_Rides", y = "Average_Fare",data = Pyber_Bubble_Plot, fit_reg = False, hue = "Type")
```


```python
colors = ["gold", "lightskyblue","lightcoral"]
explode = (0, 0, 0.10)
```


```python
Pyber_Bubble_Plot_Fare.index

```




    Index(['Rural', 'Suburban', 'Urban'], dtype='object', name='Type')



# % of Total Fares by City Type


```python
plt.title("% of Total Fares by City Type")
plt.pie(Pyber_Bubble_Plot_Fare['Total_Fare'], explode=explode, labels=Pyber_Bubble_Plot_Fare.index, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=120)
plt.axis("equal")
plt.savefig("%of TotalFares_by_CityType.png")
plt.show()
```


![png](output_20_0.png)


# % of Total Rides by City Type


```python
plt.title("% of Total Rides by City Type")
plt.pie(Pyber_Bubble_Plot_Type['Total_Rides'], explode=explode, labels=Pyber_Bubble_Plot_Fare.index, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=105)
plt.axis("equal")
plt.savefig("%of TotalRides_by_CityType.png")
plt.show()
```


![png](output_22_0.png)


# % of Total Drivers by City Type


```python
plt.title("% of Total Drivers by City Type")
plt.pie(Pyber_Bubble_Plot_Type['Driver_Count'], explode=explode, labels=Pyber_Bubble_Plot_Fare.index, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=130)
plt.axis("equal")
plt.savefig("%of Total Drivers by CityType.png")
plt.show()
```


![png](output_24_0.png)

