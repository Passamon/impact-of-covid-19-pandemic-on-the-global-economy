# impact-of-covid-19-pandemic-on-the-global-economy

Visualized the data in raw_data.csv by bringing up interactive plots with plotly and seaborn

## Downloading the Dataset

```python

import opendatasets as od
dataset_url = 'https://www.kaggle.com/shashwatwork/impact-of-covid19-pandemic-on-the-global-economy' 
od.download(dataset_url)

```
![table of raw data](https://i.ibb.co/JC1YdjV/99-B938-E1-99-A1-47-E8-A6-E9-9764-CB1972-EA.jpg)

## Exploratory Analysis and Visualization

This graph show relationship between date and TC(calcularate from total_cases). You can see at the beginning, TC is sharply increasing in each country ,and the after that TC is almost constant.

```python

fig = px.line(impact_of_covid19_raw, x="date", y="TC", color="location", 
              title='Relationship between date and TC',
              template="simple_white")
fig.show()

```

![table of raw data](https://i.ibb.co/rw1Vd5D/TC.jpg)

This graph show relationship between date and TD(calcularate from total_deaths). You can see at the beginning, TD is sharply increasing in each country ,and the after that TD is almost constant or slight increase.If you consider graph of TC and TD ,you will see relation between TC and TD because TD fluctuate by TC.

![](https://i.ibb.co/CHHdsbm/TD.jpg)

This graph show relationship between date and STI(calcularate from stringency_index). You can see STI is rising ,but after September, STI is falling in some country.

![](https://i.ibb.co/rsh7HPQ/STI.jpg)

This graph show relationship between date and HDI. You can see this graph is constant.

![](https://i.ibb.co/0Vwgz50/HDI.jpg)

This graph show between relationship between date and GDPCAP. You can see this graph is contant. If you plot graph between GDPCAP and HDI in dataframe of impact_of_covid19_transform is below ,you will see relation. 

![](https://i.ibb.co/SvSQjsm/GDPCAP.jpg)

HDI is vary by GDPCAP because if GDPCAP is high ,HDI in that country will be high.

![](https://i.ibb.co/0rsFsh7/GDPCAPHDI.jpg)

### Correlation of each data

```python

plt.figure(figsize=(10,5))
corr_cols = ["TC", "TD", "STI", "POP", "HDI", "GDPCAP"]
sns.clustermap(impact_of_covid19_raw[corr_cols].corr(),annot = True,cmap = "Reds")
sns.set(font_scale=1.4)

```

There are correlation between "TC" ,"TD" and STI ,and correlation between "GDPCAP" ,"HDI" and POP

![](https://i.ibb.co/gSgSN8X/HEAT.jpg)

## Using geopandas function for showing the golbal area

This area show relationship between HDI and date. if the area has bright colour ,it will get high value. 

```python

HDI = px.choropleth(impact_of_covid19_raw, locationmode='ISO-3', locations='iso_code',
                   color='HDI',
                   hover_name='location',hover_data=['TC','TD','STI','POP','GDPCAP'],
                   animation_frame='date', projection= 'natural earth',
                   title='HDI by date')
HDI.show()

```

![](https://i.ibb.co/p00DGhF/HDI.jpg)

This area show relationship between GDPCAP and date.

![](https://i.ibb.co/kBSL5Dt/GDPCAP.jpg)

This area show relationship between STI and date.

![](https://i.ibb.co/3Cq7YtQ/STI.jpg)

This area show relationship between TC and date.

![](https://i.ibb.co/60d3N4Q/TC.jpg)

This area show relationship between TD and date.

![](https://i.ibb.co/KGDFsQV/TD.jpg)















