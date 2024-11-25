```python
import numpy as np 
import pandas as pd
import matplotlib.pyplot as plt
import seaborn as sns

```


```python
dataset = pd.read_csv("V:/7 Mentors/stats/electronics.csv")
```


```python
dataset
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
      <th>item_id</th>
      <th>user_id</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>model_attr</th>
      <th>category</th>
      <th>brand</th>
      <th>year</th>
      <th>user_attr</th>
      <th>split</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>0</td>
      <td>5.0</td>
      <td>1999-06-13</td>
      <td>Female</td>
      <td>Portable Audio &amp; Video</td>
      <td>NaN</td>
      <td>1999</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>0</td>
      <td>1</td>
      <td>5.0</td>
      <td>1999-06-14</td>
      <td>Female</td>
      <td>Portable Audio &amp; Video</td>
      <td>NaN</td>
      <td>1999</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>0</td>
      <td>2</td>
      <td>3.0</td>
      <td>1999-06-17</td>
      <td>Female</td>
      <td>Portable Audio &amp; Video</td>
      <td>NaN</td>
      <td>1999</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>0</td>
      <td>3</td>
      <td>1.0</td>
      <td>1999-07-01</td>
      <td>Female</td>
      <td>Portable Audio &amp; Video</td>
      <td>NaN</td>
      <td>1999</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>4</td>
      <td>2.0</td>
      <td>1999-07-06</td>
      <td>Female</td>
      <td>Portable Audio &amp; Video</td>
      <td>NaN</td>
      <td>1999</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1292949</th>
      <td>9478</td>
      <td>1157628</td>
      <td>1.0</td>
      <td>2018-09-26</td>
      <td>Female</td>
      <td>Headphones</td>
      <td>Etre Jeune</td>
      <td>2017</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1292950</th>
      <td>9435</td>
      <td>1157629</td>
      <td>5.0</td>
      <td>2018-09-26</td>
      <td>Female</td>
      <td>Computers &amp; Accessories</td>
      <td>NaN</td>
      <td>2017</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1292951</th>
      <td>9305</td>
      <td>1157630</td>
      <td>3.0</td>
      <td>2018-09-26</td>
      <td>Female</td>
      <td>Computers &amp; Accessories</td>
      <td>NaN</td>
      <td>2016</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1292952</th>
      <td>9303</td>
      <td>1157631</td>
      <td>5.0</td>
      <td>2018-09-29</td>
      <td>Male</td>
      <td>Headphones</td>
      <td>NaN</td>
      <td>2018</td>
      <td>NaN</td>
      <td>0</td>
    </tr>
    <tr>
      <th>1292953</th>
      <td>9478</td>
      <td>1157632</td>
      <td>1.0</td>
      <td>2018-10-01</td>
      <td>Female</td>
      <td>Headphones</td>
      <td>Etre Jeune</td>
      <td>2017</td>
      <td>Female</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
<p>1292954 rows × 10 columns</p>
</div>




```python
dataset.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1292954 entries, 0 to 1292953
    Data columns (total 10 columns):
     #   Column      Non-Null Count    Dtype  
    ---  ------      --------------    -----  
     0   item_id     1292954 non-null  int64  
     1   user_id     1292954 non-null  int64  
     2   rating      1292954 non-null  float64
     3   timestamp   1292954 non-null  object 
     4   model_attr  1292954 non-null  object 
     5   category    1292954 non-null  object 
     6   brand       331120 non-null   object 
     7   year        1292954 non-null  int64  
     8   user_attr   174124 non-null   object 
     9   split       1292954 non-null  int64  
    dtypes: float64(1), int64(4), object(5)
    memory usage: 98.6+ MB
    


```python
from datetime import datetime
pd.to_datetime(dataset['timestamp'])
```




    0         1999-06-13
    1         1999-06-14
    2         1999-06-17
    3         1999-07-01
    4         1999-07-06
                 ...    
    1292949   2018-09-26
    1292950   2018-09-26
    1292951   2018-09-26
    1292952   2018-09-29
    1292953   2018-10-01
    Name: timestamp, Length: 1292954, dtype: datetime64[ns]




```python
dataset['brand'] = dataset['brand'].astype(str)
```


```python
dataset['category'] = dataset['category'].astype(str)
```


```python
dataset['category'] = dataset['category'].astype(str)
```


```python
dataset['user_id'] = dataset['user_id'].astype(str)
```


```python
dataset['item_id'] = dataset['item_id'].astype(str)
```


```python
dataset.columns
```




    Index(['item_id', 'user_id', 'rating', 'timestamp', 'model_attr', 'category',
           'brand', 'year', 'user_attr', 'split'],
          dtype='object')




```python
len(dataset.columns)
```




    10




```python
dataset.isna()
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
      <th>item_id</th>
      <th>user_id</th>
      <th>rating</th>
      <th>timestamp</th>
      <th>model_attr</th>
      <th>category</th>
      <th>brand</th>
      <th>year</th>
      <th>user_attr</th>
      <th>split</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>3</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>...</th>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>1292949</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1292950</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1292951</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1292952</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>True</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1292953</th>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
<p>1292954 rows × 10 columns</p>
</div>




```python
dataset.isna().sum()
```




    item_id             0
    user_id             0
    rating              0
    timestamp           0
    model_attr          0
    category            0
    brand               0
    year                0
    user_attr     1118830
    split               0
    dtype: int64




```python
sns.countplot(x='rating',data=dataset)
```




    <Axes: xlabel='rating', ylabel='count'>




    
![png](output_14_1.png)
    



```python
dataset['year'] = pd.DatetimeIndex(dataset['timestamp']).year
dataset.groupby('year')['rating'].count().plot(kind='bar')
```




    <Axes: xlabel='year'>




    
![png](output_15_1.png)
    



```python
dataset_2015 = dataset[dataset['year']  == 2015]
dataset_2015.groupby('brand')['rating'].count().sort_values(ascending=True).head(10).plot(kind='bar')
```




    <Axes: xlabel='brand'>




    
![png](output_16_1.png)
    



```python
dataset_2016 = dataset[dataset['year']  == 2016]

dataset_2016.groupby('brand')['rating'].count().sort_values(ascending=True).head(10).plot(kind='bar')
```




    <Axes: xlabel='brand'>




    
![png](output_17_1.png)
    



```python
dataset_2017 = dataset[dataset['year'] == 2017]
dataset_2017.groupby('brand')['rating'].count().sort_values(ascending=True).head(3).plot(kind = 'bar')
```




    <Axes: xlabel='brand'>




    
![png](output_18_1.png)
    



```python
dataset_2018 = dataset[dataset['year'] == 2018]
dataset_2018.groupby('brand')['rating'].count().sort_values(ascending=True).head().plot(kind='bar')
```




    <Axes: xlabel='brand'>




    
![png](output_19_1.png)
    



```python
dataset[dataset['year'] == 2015].groupby('year')['rating'].count().plot(kind = 'bar')
```




    <Axes: xlabel='year'>




    
![png](output_20_1.png)
    



```python
dataset['month'] = pd.DatetimeIndex(dataset['timestamp']).month
dataset.groupby('month')['rating'].count().plot(kind = 'bar')
```




    <Axes: xlabel='month'>




    
![png](output_21_1.png)
    



```python
dataset.groupby('brand')['rating'].count().sort_values(ascending= True).head(10).plot(kind= 'bar')
```




    <Axes: xlabel='brand'>




    
![png](output_22_1.png)
    



```python
#what product by category sold most?
dataset.groupby('category')['rating'].count().sort_values(ascending= True).head(10).plot(kind= 'bar')
```




    <Axes: xlabel='category'>




    
![png](output_23_1.png)
    



```python
#what product by brand sol;t the least?
dataset.groupby('brand')['rating'].count().sort_values(ascending=True).head(10).plot(kind = 'bar')
                                                                             
```




    <Axes: xlabel='brand'>




    
![png](output_24_1.png)
    



```python
#what product by category sold the least?
dataset.groupby('category')['rating'].count().sort_values(ascending=True).plot(kind = 'bar')
```




    <Axes: xlabel='category'>




    
![png](output_25_1.png)
    



```python
# category precentage sales?
dataset.groupby('category')['rating'].count().sort_values(ascending = True).head(5).plot(kind = 'pie' , autopct = '%1.2f%%')
```




    <Axes: ylabel='rating'>




    
![png](output_26_1.png)
    



```python
dataset.groupby('brand')['rating'].count().sort_values(ascending = True).head(5).plot(kind = 'pie' , autopct = '%1.2f%%')
```




    <Axes: ylabel='rating'>




    
![png](output_27_1.png)
    



```python

```
