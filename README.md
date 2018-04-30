# test

# A case study of wines 

## winequality-red.csv and winequality-white.csv


```python
import pandas as pd 
import numpy as np
import matplotlib.pyplot as plt
%matplotlib inline
```


```python
red_df = pd.read_csv("winequality-red.csv",sep=';')
white_df = pd.read_csv("winequality-white.csv",sep=';')
```


```python
red_df.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed_acidity</th>
      <th>volatile_acidity</th>
      <th>citric_acid</th>
      <th>residual_sugar</th>
      <th>chlorides</th>
      <th>free_sulfur_dioxide</th>
      <th>total_sulfur-dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.70</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.9978</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.88</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.9968</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>9.8</td>
      <td>5</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.76</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.9970</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>9.8</td>
      <td>5</td>
    </tr>
  </tbody>
</table>
</div>




```python
white_df.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed_acidity</th>
      <th>volatile_acidity</th>
      <th>citric_acid</th>
      <th>residual_sugar</th>
      <th>chlorides</th>
      <th>free_sulfur_dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.0</td>
      <td>0.27</td>
      <td>0.36</td>
      <td>20.7</td>
      <td>0.045</td>
      <td>45.0</td>
      <td>170.0</td>
      <td>1.0010</td>
      <td>3.00</td>
      <td>0.45</td>
      <td>8.8</td>
      <td>6</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6.3</td>
      <td>0.30</td>
      <td>0.34</td>
      <td>1.6</td>
      <td>0.049</td>
      <td>14.0</td>
      <td>132.0</td>
      <td>0.9940</td>
      <td>3.30</td>
      <td>0.49</td>
      <td>9.5</td>
      <td>6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8.1</td>
      <td>0.28</td>
      <td>0.40</td>
      <td>6.9</td>
      <td>0.050</td>
      <td>30.0</td>
      <td>97.0</td>
      <td>0.9951</td>
      <td>3.26</td>
      <td>0.44</td>
      <td>10.1</td>
      <td>6</td>
    </tr>
  </tbody>
</table>
</div>




```python
red_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 1599 entries, 0 to 1598
    Data columns (total 12 columns):
    fixed_acidity           1599 non-null float64
    volatile_acidity        1599 non-null float64
    citric_acid             1599 non-null float64
    residual_sugar          1599 non-null float64
    chlorides               1599 non-null float64
    free_sulfur_dioxide     1599 non-null float64
    total_sulfur-dioxide    1599 non-null float64
    density                 1599 non-null float64
    pH                      1599 non-null float64
    sulphates               1599 non-null float64
    alcohol                 1599 non-null float64
    quality                 1599 non-null int64
    dtypes: float64(11), int64(1)
    memory usage: 150.0 KB
    


```python
white_df.info()
```

    <class 'pandas.core.frame.DataFrame'>
    RangeIndex: 4898 entries, 0 to 4897
    Data columns (total 12 columns):
    fixed_acidity           4898 non-null float64
    volatile_acidity        4898 non-null float64
    citric_acid             4898 non-null float64
    residual_sugar          4898 non-null float64
    chlorides               4898 non-null float64
    free_sulfur_dioxide     4898 non-null float64
    total_sulfur_dioxide    4898 non-null float64
    density                 4898 non-null float64
    pH                      4898 non-null float64
    sulphates               4898 non-null float64
    alcohol                 4898 non-null float64
    quality                 4898 non-null int64
    dtypes: float64(11), int64(1)
    memory usage: 459.3 KB
    


```python
red_df.shape
```




    (1599, 12)




```python
white_df.shape
```




    (4898, 12)



# Creating color columns


```python
red_list = ['red']*len(red_df.index)
color_red = np.array(red_list)

```


```python
white_list = ['white']*len(white_df.index)
color_white = np.array(white_list)
```


```python
red_df['color_red'] = color_red
red_df.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed_acidity</th>
      <th>volatile_acidity</th>
      <th>citric_acid</th>
      <th>residual_sugar</th>
      <th>chlorides</th>
      <th>free_sulfur_dioxide</th>
      <th>total_sulfur-dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
      <th>color_red</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.4</td>
      <td>0.70</td>
      <td>0.00</td>
      <td>1.9</td>
      <td>0.076</td>
      <td>11.0</td>
      <td>34.0</td>
      <td>0.9978</td>
      <td>3.51</td>
      <td>0.56</td>
      <td>9.4</td>
      <td>5</td>
      <td>red</td>
    </tr>
    <tr>
      <th>1</th>
      <td>7.8</td>
      <td>0.88</td>
      <td>0.00</td>
      <td>2.6</td>
      <td>0.098</td>
      <td>25.0</td>
      <td>67.0</td>
      <td>0.9968</td>
      <td>3.20</td>
      <td>0.68</td>
      <td>9.8</td>
      <td>5</td>
      <td>red</td>
    </tr>
    <tr>
      <th>2</th>
      <td>7.8</td>
      <td>0.76</td>
      <td>0.04</td>
      <td>2.3</td>
      <td>0.092</td>
      <td>15.0</td>
      <td>54.0</td>
      <td>0.9970</td>
      <td>3.26</td>
      <td>0.65</td>
      <td>9.8</td>
      <td>5</td>
      <td>red</td>
    </tr>
  </tbody>
</table>
</div>




```python
white_df['color_white'] = color_white
white_df.head(3)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>fixed_acidity</th>
      <th>volatile_acidity</th>
      <th>citric_acid</th>
      <th>residual_sugar</th>
      <th>chlorides</th>
      <th>free_sulfur_dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>density</th>
      <th>pH</th>
      <th>sulphates</th>
      <th>alcohol</th>
      <th>quality</th>
      <th>color_white</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>7.0</td>
      <td>0.27</td>
      <td>0.36</td>
      <td>20.7</td>
      <td>0.045</td>
      <td>45.0</td>
      <td>170.0</td>
      <td>1.0010</td>
      <td>3.00</td>
      <td>0.45</td>
      <td>8.8</td>
      <td>6</td>
      <td>white</td>
    </tr>
    <tr>
      <th>1</th>
      <td>6.3</td>
      <td>0.30</td>
      <td>0.34</td>
      <td>1.6</td>
      <td>0.049</td>
      <td>14.0</td>
      <td>132.0</td>
      <td>0.9940</td>
      <td>3.30</td>
      <td>0.49</td>
      <td>9.5</td>
      <td>6</td>
      <td>white</td>
    </tr>
    <tr>
      <th>2</th>
      <td>8.1</td>
      <td>0.28</td>
      <td>0.40</td>
      <td>6.9</td>
      <td>0.050</td>
      <td>30.0</td>
      <td>97.0</td>
      <td>0.9951</td>
      <td>3.26</td>
      <td>0.44</td>
      <td>10.1</td>
      <td>6</td>
      <td>white</td>
    </tr>
  </tbody>
</table>
</div>



### Appending Data 


```python
df = red_df.append(white_df,ignore_index=True)
```


```python
df
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>color_red</th>
      <th>color_white</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9.400000</td>
      <td>0.076</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99780</td>
      <td>7.4</td>
      <td>11.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.90</td>
      <td>0.56</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>0.700</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9.800000</td>
      <td>0.098</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>7.8</td>
      <td>25.0</td>
      <td>3.20</td>
      <td>5</td>
      <td>2.60</td>
      <td>0.68</td>
      <td>67.0</td>
      <td>NaN</td>
      <td>0.880</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9.800000</td>
      <td>0.092</td>
      <td>0.04</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99700</td>
      <td>7.8</td>
      <td>15.0</td>
      <td>3.26</td>
      <td>5</td>
      <td>2.30</td>
      <td>0.65</td>
      <td>54.0</td>
      <td>NaN</td>
      <td>0.760</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.800000</td>
      <td>0.075</td>
      <td>0.56</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99800</td>
      <td>11.2</td>
      <td>17.0</td>
      <td>3.16</td>
      <td>6</td>
      <td>1.90</td>
      <td>0.58</td>
      <td>60.0</td>
      <td>NaN</td>
      <td>0.280</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9.400000</td>
      <td>0.076</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99780</td>
      <td>7.4</td>
      <td>11.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.90</td>
      <td>0.56</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>0.700</td>
    </tr>
    <tr>
      <th>5</th>
      <td>9.400000</td>
      <td>0.075</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99780</td>
      <td>7.4</td>
      <td>13.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.80</td>
      <td>0.56</td>
      <td>40.0</td>
      <td>NaN</td>
      <td>0.660</td>
    </tr>
    <tr>
      <th>6</th>
      <td>9.400000</td>
      <td>0.069</td>
      <td>0.06</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99640</td>
      <td>7.9</td>
      <td>15.0</td>
      <td>3.30</td>
      <td>5</td>
      <td>1.60</td>
      <td>0.46</td>
      <td>59.0</td>
      <td>NaN</td>
      <td>0.600</td>
    </tr>
    <tr>
      <th>7</th>
      <td>10.000000</td>
      <td>0.065</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99460</td>
      <td>7.3</td>
      <td>15.0</td>
      <td>3.39</td>
      <td>7</td>
      <td>1.20</td>
      <td>0.47</td>
      <td>21.0</td>
      <td>NaN</td>
      <td>0.650</td>
    </tr>
    <tr>
      <th>8</th>
      <td>9.500000</td>
      <td>0.073</td>
      <td>0.02</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>7.8</td>
      <td>9.0</td>
      <td>3.36</td>
      <td>7</td>
      <td>2.00</td>
      <td>0.57</td>
      <td>18.0</td>
      <td>NaN</td>
      <td>0.580</td>
    </tr>
    <tr>
      <th>9</th>
      <td>10.500000</td>
      <td>0.071</td>
      <td>0.36</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99780</td>
      <td>7.5</td>
      <td>17.0</td>
      <td>3.35</td>
      <td>5</td>
      <td>6.10</td>
      <td>0.80</td>
      <td>102.0</td>
      <td>NaN</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>10</th>
      <td>9.200000</td>
      <td>0.097</td>
      <td>0.08</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99590</td>
      <td>6.7</td>
      <td>15.0</td>
      <td>3.28</td>
      <td>5</td>
      <td>1.80</td>
      <td>0.54</td>
      <td>65.0</td>
      <td>NaN</td>
      <td>0.580</td>
    </tr>
    <tr>
      <th>11</th>
      <td>10.500000</td>
      <td>0.071</td>
      <td>0.36</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99780</td>
      <td>7.5</td>
      <td>17.0</td>
      <td>3.35</td>
      <td>5</td>
      <td>6.10</td>
      <td>0.80</td>
      <td>102.0</td>
      <td>NaN</td>
      <td>0.500</td>
    </tr>
    <tr>
      <th>12</th>
      <td>9.900000</td>
      <td>0.089</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99430</td>
      <td>5.6</td>
      <td>16.0</td>
      <td>3.58</td>
      <td>5</td>
      <td>1.60</td>
      <td>0.52</td>
      <td>59.0</td>
      <td>NaN</td>
      <td>0.615</td>
    </tr>
    <tr>
      <th>13</th>
      <td>9.100000</td>
      <td>0.114</td>
      <td>0.29</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99740</td>
      <td>7.8</td>
      <td>9.0</td>
      <td>3.26</td>
      <td>5</td>
      <td>1.60</td>
      <td>1.56</td>
      <td>29.0</td>
      <td>NaN</td>
      <td>0.610</td>
    </tr>
    <tr>
      <th>14</th>
      <td>9.200000</td>
      <td>0.176</td>
      <td>0.18</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99860</td>
      <td>8.9</td>
      <td>52.0</td>
      <td>3.16</td>
      <td>5</td>
      <td>3.80</td>
      <td>0.88</td>
      <td>145.0</td>
      <td>NaN</td>
      <td>0.620</td>
    </tr>
    <tr>
      <th>15</th>
      <td>9.200000</td>
      <td>0.170</td>
      <td>0.19</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99860</td>
      <td>8.9</td>
      <td>51.0</td>
      <td>3.17</td>
      <td>5</td>
      <td>3.90</td>
      <td>0.93</td>
      <td>148.0</td>
      <td>NaN</td>
      <td>0.620</td>
    </tr>
    <tr>
      <th>16</th>
      <td>10.500000</td>
      <td>0.092</td>
      <td>0.56</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99690</td>
      <td>8.5</td>
      <td>35.0</td>
      <td>3.30</td>
      <td>7</td>
      <td>1.80</td>
      <td>0.75</td>
      <td>103.0</td>
      <td>NaN</td>
      <td>0.280</td>
    </tr>
    <tr>
      <th>17</th>
      <td>9.300000</td>
      <td>0.368</td>
      <td>0.28</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>8.1</td>
      <td>16.0</td>
      <td>3.11</td>
      <td>5</td>
      <td>1.70</td>
      <td>1.28</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>0.560</td>
    </tr>
    <tr>
      <th>18</th>
      <td>9.000000</td>
      <td>0.086</td>
      <td>0.08</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99740</td>
      <td>7.4</td>
      <td>6.0</td>
      <td>3.38</td>
      <td>4</td>
      <td>4.40</td>
      <td>0.50</td>
      <td>29.0</td>
      <td>NaN</td>
      <td>0.590</td>
    </tr>
    <tr>
      <th>19</th>
      <td>9.200000</td>
      <td>0.341</td>
      <td>0.51</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99690</td>
      <td>7.9</td>
      <td>17.0</td>
      <td>3.04</td>
      <td>6</td>
      <td>1.80</td>
      <td>1.08</td>
      <td>56.0</td>
      <td>NaN</td>
      <td>0.320</td>
    </tr>
    <tr>
      <th>20</th>
      <td>9.400000</td>
      <td>0.077</td>
      <td>0.48</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>8.9</td>
      <td>29.0</td>
      <td>3.39</td>
      <td>6</td>
      <td>1.80</td>
      <td>0.53</td>
      <td>60.0</td>
      <td>NaN</td>
      <td>0.220</td>
    </tr>
    <tr>
      <th>21</th>
      <td>9.700000</td>
      <td>0.082</td>
      <td>0.31</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99820</td>
      <td>7.6</td>
      <td>23.0</td>
      <td>3.52</td>
      <td>5</td>
      <td>2.30</td>
      <td>0.65</td>
      <td>71.0</td>
      <td>NaN</td>
      <td>0.390</td>
    </tr>
    <tr>
      <th>22</th>
      <td>9.500000</td>
      <td>0.106</td>
      <td>0.21</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99660</td>
      <td>7.9</td>
      <td>10.0</td>
      <td>3.17</td>
      <td>5</td>
      <td>1.60</td>
      <td>0.91</td>
      <td>37.0</td>
      <td>NaN</td>
      <td>0.430</td>
    </tr>
    <tr>
      <th>23</th>
      <td>9.400000</td>
      <td>0.084</td>
      <td>0.11</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>8.5</td>
      <td>9.0</td>
      <td>3.17</td>
      <td>5</td>
      <td>2.30</td>
      <td>0.53</td>
      <td>67.0</td>
      <td>NaN</td>
      <td>0.490</td>
    </tr>
    <tr>
      <th>24</th>
      <td>9.700000</td>
      <td>0.085</td>
      <td>0.14</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99680</td>
      <td>6.9</td>
      <td>21.0</td>
      <td>3.43</td>
      <td>6</td>
      <td>2.40</td>
      <td>0.63</td>
      <td>40.0</td>
      <td>NaN</td>
      <td>0.400</td>
    </tr>
    <tr>
      <th>25</th>
      <td>9.300000</td>
      <td>0.080</td>
      <td>0.16</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99550</td>
      <td>6.3</td>
      <td>11.0</td>
      <td>3.34</td>
      <td>5</td>
      <td>1.40</td>
      <td>0.56</td>
      <td>23.0</td>
      <td>NaN</td>
      <td>0.390</td>
    </tr>
    <tr>
      <th>26</th>
      <td>9.500000</td>
      <td>0.080</td>
      <td>0.24</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99620</td>
      <td>7.6</td>
      <td>4.0</td>
      <td>3.28</td>
      <td>5</td>
      <td>1.80</td>
      <td>0.59</td>
      <td>11.0</td>
      <td>NaN</td>
      <td>0.410</td>
    </tr>
    <tr>
      <th>27</th>
      <td>9.500000</td>
      <td>0.106</td>
      <td>0.21</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99660</td>
      <td>7.9</td>
      <td>10.0</td>
      <td>3.17</td>
      <td>5</td>
      <td>1.60</td>
      <td>0.91</td>
      <td>37.0</td>
      <td>NaN</td>
      <td>0.430</td>
    </tr>
    <tr>
      <th>28</th>
      <td>9.400000</td>
      <td>0.080</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99720</td>
      <td>7.1</td>
      <td>14.0</td>
      <td>3.47</td>
      <td>5</td>
      <td>1.90</td>
      <td>0.55</td>
      <td>35.0</td>
      <td>NaN</td>
      <td>0.710</td>
    </tr>
    <tr>
      <th>29</th>
      <td>9.800000</td>
      <td>0.082</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.99640</td>
      <td>7.8</td>
      <td>8.0</td>
      <td>3.38</td>
      <td>6</td>
      <td>2.00</td>
      <td>0.59</td>
      <td>16.0</td>
      <td>NaN</td>
      <td>0.645</td>
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
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
      <td>...</td>
    </tr>
    <tr>
      <th>6467</th>
      <td>10.800000</td>
      <td>0.046</td>
      <td>0.31</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99324</td>
      <td>5.8</td>
      <td>42.0</td>
      <td>3.31</td>
      <td>6</td>
      <td>4.50</td>
      <td>0.64</td>
      <td>NaN</td>
      <td>124.0</td>
      <td>0.230</td>
    </tr>
    <tr>
      <th>6468</th>
      <td>9.800000</td>
      <td>0.032</td>
      <td>0.33</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99626</td>
      <td>6.6</td>
      <td>8.0</td>
      <td>3.19</td>
      <td>6</td>
      <td>10.10</td>
      <td>0.51</td>
      <td>NaN</td>
      <td>81.0</td>
      <td>0.240</td>
    </tr>
    <tr>
      <th>6469</th>
      <td>11.450000</td>
      <td>0.021</td>
      <td>0.28</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99188</td>
      <td>6.1</td>
      <td>29.0</td>
      <td>3.15</td>
      <td>7</td>
      <td>6.60</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>132.0</td>
      <td>0.320</td>
    </tr>
    <tr>
      <th>6470</th>
      <td>12.050000</td>
      <td>0.015</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98970</td>
      <td>5.0</td>
      <td>20.0</td>
      <td>3.37</td>
      <td>6</td>
      <td>1.90</td>
      <td>0.55</td>
      <td>NaN</td>
      <td>98.0</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>6471</th>
      <td>9.700000</td>
      <td>0.032</td>
      <td>0.41</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99622</td>
      <td>6.0</td>
      <td>50.0</td>
      <td>3.14</td>
      <td>5</td>
      <td>12.40</td>
      <td>0.60</td>
      <td>NaN</td>
      <td>179.0</td>
      <td>0.420</td>
    </tr>
    <tr>
      <th>6472</th>
      <td>11.900000</td>
      <td>0.030</td>
      <td>0.32</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99044</td>
      <td>5.7</td>
      <td>33.0</td>
      <td>3.33</td>
      <td>6</td>
      <td>1.60</td>
      <td>0.52</td>
      <td>NaN</td>
      <td>122.0</td>
      <td>0.210</td>
    </tr>
    <tr>
      <th>6473</th>
      <td>10.000000</td>
      <td>0.048</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99282</td>
      <td>5.6</td>
      <td>16.0</td>
      <td>3.49</td>
      <td>6</td>
      <td>2.50</td>
      <td>0.49</td>
      <td>NaN</td>
      <td>125.0</td>
      <td>0.200</td>
    </tr>
    <tr>
      <th>6474</th>
      <td>9.700000</td>
      <td>0.035</td>
      <td>0.26</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99245</td>
      <td>7.4</td>
      <td>18.0</td>
      <td>3.12</td>
      <td>6</td>
      <td>1.20</td>
      <td>0.41</td>
      <td>NaN</td>
      <td>97.0</td>
      <td>0.220</td>
    </tr>
    <tr>
      <th>6475</th>
      <td>11.600000</td>
      <td>0.038</td>
      <td>0.42</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99132</td>
      <td>6.2</td>
      <td>34.0</td>
      <td>3.36</td>
      <td>7</td>
      <td>2.50</td>
      <td>0.59</td>
      <td>NaN</td>
      <td>117.0</td>
      <td>0.380</td>
    </tr>
    <tr>
      <th>6476</th>
      <td>8.800000</td>
      <td>0.032</td>
      <td>0.00</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99286</td>
      <td>5.9</td>
      <td>12.0</td>
      <td>3.25</td>
      <td>5</td>
      <td>0.80</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>82.0</td>
      <td>0.540</td>
    </tr>
    <tr>
      <th>6477</th>
      <td>9.500000</td>
      <td>0.035</td>
      <td>0.02</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99234</td>
      <td>6.2</td>
      <td>6.0</td>
      <td>3.24</td>
      <td>4</td>
      <td>0.90</td>
      <td>0.35</td>
      <td>NaN</td>
      <td>81.0</td>
      <td>0.530</td>
    </tr>
    <tr>
      <th>6478</th>
      <td>9.533333</td>
      <td>0.046</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99494</td>
      <td>6.6</td>
      <td>68.0</td>
      <td>3.15</td>
      <td>6</td>
      <td>8.10</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>170.0</td>
      <td>0.340</td>
    </tr>
    <tr>
      <th>6479</th>
      <td>9.533333</td>
      <td>0.046</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99494</td>
      <td>6.6</td>
      <td>68.0</td>
      <td>3.15</td>
      <td>6</td>
      <td>8.10</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>170.0</td>
      <td>0.340</td>
    </tr>
    <tr>
      <th>6480</th>
      <td>9.400000</td>
      <td>0.030</td>
      <td>0.27</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99540</td>
      <td>5.0</td>
      <td>34.0</td>
      <td>3.07</td>
      <td>6</td>
      <td>11.75</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>118.0</td>
      <td>0.235</td>
    </tr>
    <tr>
      <th>6481</th>
      <td>10.700000</td>
      <td>0.037</td>
      <td>0.13</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99184</td>
      <td>5.5</td>
      <td>45.0</td>
      <td>3.26</td>
      <td>5</td>
      <td>1.30</td>
      <td>0.38</td>
      <td>NaN</td>
      <td>156.0</td>
      <td>0.320</td>
    </tr>
    <tr>
      <th>6482</th>
      <td>11.500000</td>
      <td>0.035</td>
      <td>0.17</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98964</td>
      <td>4.9</td>
      <td>60.0</td>
      <td>3.27</td>
      <td>6</td>
      <td>1.90</td>
      <td>0.35</td>
      <td>NaN</td>
      <td>148.0</td>
      <td>0.470</td>
    </tr>
    <tr>
      <th>6483</th>
      <td>9.600000</td>
      <td>0.048</td>
      <td>0.38</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99492</td>
      <td>6.5</td>
      <td>68.0</td>
      <td>3.14</td>
      <td>5</td>
      <td>8.30</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>174.0</td>
      <td>0.330</td>
    </tr>
    <tr>
      <th>6484</th>
      <td>9.550000</td>
      <td>0.046</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99494</td>
      <td>6.6</td>
      <td>68.0</td>
      <td>3.15</td>
      <td>6</td>
      <td>8.10</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>170.0</td>
      <td>0.340</td>
    </tr>
    <tr>
      <th>6485</th>
      <td>12.150000</td>
      <td>0.028</td>
      <td>0.28</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99168</td>
      <td>6.2</td>
      <td>45.0</td>
      <td>3.21</td>
      <td>7</td>
      <td>5.70</td>
      <td>1.08</td>
      <td>NaN</td>
      <td>121.0</td>
      <td>0.210</td>
    </tr>
    <tr>
      <th>6486</th>
      <td>13.000000</td>
      <td>0.023</td>
      <td>0.22</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98928</td>
      <td>6.2</td>
      <td>5.0</td>
      <td>3.04</td>
      <td>7</td>
      <td>1.90</td>
      <td>0.79</td>
      <td>NaN</td>
      <td>56.0</td>
      <td>0.410</td>
    </tr>
    <tr>
      <th>6487</th>
      <td>9.200000</td>
      <td>0.052</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99330</td>
      <td>6.8</td>
      <td>38.0</td>
      <td>3.04</td>
      <td>5</td>
      <td>1.20</td>
      <td>0.54</td>
      <td>NaN</td>
      <td>127.0</td>
      <td>0.220</td>
    </tr>
    <tr>
      <th>6488</th>
      <td>9.400000</td>
      <td>0.030</td>
      <td>0.27</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99540</td>
      <td>4.9</td>
      <td>34.0</td>
      <td>3.07</td>
      <td>6</td>
      <td>11.75</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>118.0</td>
      <td>0.235</td>
    </tr>
    <tr>
      <th>6489</th>
      <td>11.800000</td>
      <td>0.036</td>
      <td>0.29</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98938</td>
      <td>6.1</td>
      <td>25.0</td>
      <td>3.06</td>
      <td>6</td>
      <td>2.20</td>
      <td>0.44</td>
      <td>NaN</td>
      <td>100.0</td>
      <td>0.340</td>
    </tr>
    <tr>
      <th>6490</th>
      <td>10.600000</td>
      <td>0.038</td>
      <td>0.32</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99074</td>
      <td>5.7</td>
      <td>38.0</td>
      <td>3.24</td>
      <td>6</td>
      <td>0.90</td>
      <td>0.46</td>
      <td>NaN</td>
      <td>121.0</td>
      <td>0.210</td>
    </tr>
    <tr>
      <th>6491</th>
      <td>9.700000</td>
      <td>0.032</td>
      <td>0.38</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99298</td>
      <td>6.5</td>
      <td>29.0</td>
      <td>3.29</td>
      <td>5</td>
      <td>1.30</td>
      <td>0.54</td>
      <td>NaN</td>
      <td>112.0</td>
      <td>0.230</td>
    </tr>
    <tr>
      <th>6492</th>
      <td>11.200000</td>
      <td>0.039</td>
      <td>0.29</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99114</td>
      <td>6.2</td>
      <td>24.0</td>
      <td>3.27</td>
      <td>6</td>
      <td>1.60</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>92.0</td>
      <td>0.210</td>
    </tr>
    <tr>
      <th>6493</th>
      <td>9.600000</td>
      <td>0.047</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99490</td>
      <td>6.6</td>
      <td>57.0</td>
      <td>3.15</td>
      <td>5</td>
      <td>8.00</td>
      <td>0.46</td>
      <td>NaN</td>
      <td>168.0</td>
      <td>0.320</td>
    </tr>
    <tr>
      <th>6494</th>
      <td>9.400000</td>
      <td>0.041</td>
      <td>0.19</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.99254</td>
      <td>6.5</td>
      <td>30.0</td>
      <td>2.99</td>
      <td>6</td>
      <td>1.20</td>
      <td>0.46</td>
      <td>NaN</td>
      <td>111.0</td>
      <td>0.240</td>
    </tr>
    <tr>
      <th>6495</th>
      <td>12.800000</td>
      <td>0.022</td>
      <td>0.30</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98869</td>
      <td>5.5</td>
      <td>20.0</td>
      <td>3.34</td>
      <td>7</td>
      <td>1.10</td>
      <td>0.38</td>
      <td>NaN</td>
      <td>110.0</td>
      <td>0.290</td>
    </tr>
    <tr>
      <th>6496</th>
      <td>11.800000</td>
      <td>0.020</td>
      <td>0.38</td>
      <td>NaN</td>
      <td>white</td>
      <td>0.98941</td>
      <td>6.0</td>
      <td>22.0</td>
      <td>3.26</td>
      <td>6</td>
      <td>0.80</td>
      <td>0.32</td>
      <td>NaN</td>
      <td>98.0</td>
      <td>0.210</td>
    </tr>
  </tbody>
</table>
<p>6497 rows × 15 columns</p>
</div>




```python
df.to_csv('winequality-edited.csv',index=False)
```


```python
df.shape
```




    (6497, 15)



# Appending Data Continued 

# EDA WITH VISUALS


```python
df.head(2)
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>color_red</th>
      <th>color_white</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9.4</td>
      <td>0.076</td>
      <td>0.0</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9978</td>
      <td>7.4</td>
      <td>11.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.9</td>
      <td>0.56</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>0.70</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9.8</td>
      <td>0.098</td>
      <td>0.0</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9968</td>
      <td>7.8</td>
      <td>25.0</td>
      <td>3.20</td>
      <td>5</td>
      <td>2.6</td>
      <td>0.68</td>
      <td>67.0</td>
      <td>NaN</td>
      <td>0.88</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['fixed_acidity'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1e69cef8b00>




![png](case_files/case_22_1.png)



```python
df['pH'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1e69e1bb2e8>




![png](case_files/case_23_1.png)



```python
df['total_sulfur-dioxide'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1e69e21b780>




![png](case_files/case_24_1.png)



```python
df['alcohol'].hist()
```




    <matplotlib.axes._subplots.AxesSubplot at 0x1e69e5d64e0>




![png](case_files/case_25_1.png)


# scatterplots of quality Against Various Features


```python
df.plot(x='quality',y='volatile_acidity',kind='scatter');
```


![png](case_files/case_27_0.png)



```python
df.plot(x='quality',y='residual_sugar',kind='scatter',color='y');
```


![png](case_files/case_28_0.png)



```python
df.plot(x='quality',y='pH',kind='scatter',color='r');
```


![png](case_files/case_29_0.png)



```python
df.plot(x='quality',y='alcohol',kind='scatter',color='green');
```


![png](case_files/case_30_0.png)


# Drawing conclusions using groupby with pandas

## is a certain type of wine assocaited with higher quality?


```python
df.groupby('color_red').mean()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
    </tr>
    <tr>
      <th>color_red</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>red</th>
      <td>10.422983</td>
      <td>0.087467</td>
      <td>0.270976</td>
      <td>0.996747</td>
      <td>8.319637</td>
      <td>15.874922</td>
      <td>3.311113</td>
      <td>5.636023</td>
      <td>2.538806</td>
      <td>0.658149</td>
      <td>46.467792</td>
      <td>NaN</td>
      <td>0.527821</td>
    </tr>
  </tbody>
</table>
</div>




```python
df.groupby('color_white').mean()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
    </tr>
    <tr>
      <th>color_white</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>white</th>
      <td>10.514267</td>
      <td>0.045772</td>
      <td>0.334192</td>
      <td>0.994027</td>
      <td>6.854788</td>
      <td>35.308085</td>
      <td>3.188267</td>
      <td>5.877909</td>
      <td>6.391415</td>
      <td>0.489847</td>
      <td>NaN</td>
      <td>138.360657</td>
      <td>0.278241</td>
    </tr>
  </tbody>
</table>
</div>



## what level of acidity receives the highest average rating?


```python
df.describe()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>count</th>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>6497.000000</td>
      <td>1599.000000</td>
      <td>4898.000000</td>
      <td>6497.000000</td>
    </tr>
    <tr>
      <th>mean</th>
      <td>10.491801</td>
      <td>0.056034</td>
      <td>0.318633</td>
      <td>0.994697</td>
      <td>7.215307</td>
      <td>30.525319</td>
      <td>3.218501</td>
      <td>5.818378</td>
      <td>5.443235</td>
      <td>0.531268</td>
      <td>46.467792</td>
      <td>138.360657</td>
      <td>0.339666</td>
    </tr>
    <tr>
      <th>std</th>
      <td>1.192712</td>
      <td>0.035034</td>
      <td>0.145318</td>
      <td>0.002999</td>
      <td>1.296434</td>
      <td>17.749400</td>
      <td>0.160787</td>
      <td>0.873255</td>
      <td>4.757804</td>
      <td>0.148806</td>
      <td>32.895324</td>
      <td>42.498065</td>
      <td>0.164636</td>
    </tr>
    <tr>
      <th>min</th>
      <td>8.000000</td>
      <td>0.009000</td>
      <td>0.000000</td>
      <td>0.987110</td>
      <td>3.800000</td>
      <td>1.000000</td>
      <td>2.720000</td>
      <td>3.000000</td>
      <td>0.600000</td>
      <td>0.220000</td>
      <td>6.000000</td>
      <td>9.000000</td>
      <td>0.080000</td>
    </tr>
    <tr>
      <th>25%</th>
      <td>9.500000</td>
      <td>0.038000</td>
      <td>0.250000</td>
      <td>0.992340</td>
      <td>6.400000</td>
      <td>17.000000</td>
      <td>3.110000</td>
      <td>5.000000</td>
      <td>1.800000</td>
      <td>0.430000</td>
      <td>22.000000</td>
      <td>108.000000</td>
      <td>0.230000</td>
    </tr>
    <tr>
      <th>50%</th>
      <td>10.300000</td>
      <td>0.047000</td>
      <td>0.310000</td>
      <td>0.994890</td>
      <td>7.000000</td>
      <td>29.000000</td>
      <td>3.210000</td>
      <td>6.000000</td>
      <td>3.000000</td>
      <td>0.510000</td>
      <td>38.000000</td>
      <td>134.000000</td>
      <td>0.290000</td>
    </tr>
    <tr>
      <th>75%</th>
      <td>11.300000</td>
      <td>0.065000</td>
      <td>0.390000</td>
      <td>0.996990</td>
      <td>7.700000</td>
      <td>41.000000</td>
      <td>3.320000</td>
      <td>6.000000</td>
      <td>8.100000</td>
      <td>0.600000</td>
      <td>62.000000</td>
      <td>167.000000</td>
      <td>0.400000</td>
    </tr>
    <tr>
      <th>max</th>
      <td>14.900000</td>
      <td>0.611000</td>
      <td>1.660000</td>
      <td>1.038980</td>
      <td>15.900000</td>
      <td>289.000000</td>
      <td>4.010000</td>
      <td>9.000000</td>
      <td>65.800000</td>
      <td>2.000000</td>
      <td>289.000000</td>
      <td>440.000000</td>
      <td>1.580000</td>
    </tr>
  </tbody>
</table>
</div>




```python
df['pH'].describe()
```




    count    6497.000000
    mean        3.218501
    std         0.160787
    min         2.720000
    25%         3.110000
    50%         3.210000
    75%         3.320000
    max         4.010000
    Name: pH, dtype: float64




```python
# Bin edges that will be used to "cut" the data into groups
bin_edges = [2.72,3.11,3.21,3.32,4.01]
```


```python
bin_names=['fixed_acidity' ,'volatile_acidity' ,'citric_acid' ,'residual_sugar' ]
```


```python
df['acidity_levels'] = pd.cut(df['pH'], bin_edges, labels=bin_names)
```


```python
df.head()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>citric_acid</th>
      <th>color_red</th>
      <th>color_white</th>
      <th>density</th>
      <th>fixed_acidity</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>residual_sugar</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
      <th>volatile_acidity</th>
      <th>acidity_levels</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>9.4</td>
      <td>0.076</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9978</td>
      <td>7.4</td>
      <td>11.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.9</td>
      <td>0.56</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>0.70</td>
      <td>residual_sugar</td>
    </tr>
    <tr>
      <th>1</th>
      <td>9.8</td>
      <td>0.098</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9968</td>
      <td>7.8</td>
      <td>25.0</td>
      <td>3.20</td>
      <td>5</td>
      <td>2.6</td>
      <td>0.68</td>
      <td>67.0</td>
      <td>NaN</td>
      <td>0.88</td>
      <td>volatile_acidity</td>
    </tr>
    <tr>
      <th>2</th>
      <td>9.8</td>
      <td>0.092</td>
      <td>0.04</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9970</td>
      <td>7.8</td>
      <td>15.0</td>
      <td>3.26</td>
      <td>5</td>
      <td>2.3</td>
      <td>0.65</td>
      <td>54.0</td>
      <td>NaN</td>
      <td>0.76</td>
      <td>citric_acid</td>
    </tr>
    <tr>
      <th>3</th>
      <td>9.8</td>
      <td>0.075</td>
      <td>0.56</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9980</td>
      <td>11.2</td>
      <td>17.0</td>
      <td>3.16</td>
      <td>6</td>
      <td>1.9</td>
      <td>0.58</td>
      <td>60.0</td>
      <td>NaN</td>
      <td>0.28</td>
      <td>volatile_acidity</td>
    </tr>
    <tr>
      <th>4</th>
      <td>9.4</td>
      <td>0.076</td>
      <td>0.00</td>
      <td>red</td>
      <td>NaN</td>
      <td>0.9978</td>
      <td>7.4</td>
      <td>11.0</td>
      <td>3.51</td>
      <td>5</td>
      <td>1.9</td>
      <td>0.56</td>
      <td>34.0</td>
      <td>NaN</td>
      <td>0.70</td>
      <td>residual_sugar</td>
    </tr>
  </tbody>
</table>
</div>




```python
# Find the mean quality of each acidity level with groupby
df.groupby(['fixed_acidity' ,'volatile_acidity' ,'citric_acid' ,'residual_sugar' ]).mean()
```




<div>
<style>
    .dataframe thead tr:only-child th {
        text-align: right;
    }

    .dataframe thead th {
        text-align: left;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th>alcohol</th>
      <th>chlorides</th>
      <th>density</th>
      <th>free_sulfur_dioxide</th>
      <th>pH</th>
      <th>quality</th>
      <th>sulphates</th>
      <th>total_sulfur-dioxide</th>
      <th>total_sulfur_dioxide</th>
    </tr>
    <tr>
      <th>fixed_acidity</th>
      <th>volatile_acidity</th>
      <th>citric_acid</th>
      <th>residual_sugar</th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>3.8</th>
      <th>0.310</th>
      <th>0.02</th>
      <th>11.10</th>
      <td>12.400000</td>
      <td>0.036</td>
      <td>0.99248</td>
      <td>20.0</td>
      <td>3.75</td>
      <td>6.0</td>
      <td>0.44</td>
      <td>NaN</td>
      <td>114.0</td>
    </tr>
    <tr>
      <th>3.9</th>
      <th>0.225</th>
      <th>0.40</th>
      <th>4.20</th>
      <td>12.800000</td>
      <td>0.030</td>
      <td>0.98900</td>
      <td>29.0</td>
      <td>3.57</td>
      <td>8.0</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>118.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">4.2</th>
      <th>0.170</th>
      <th>0.36</th>
      <th>1.80</th>
      <td>12.000000</td>
      <td>0.029</td>
      <td>0.98999</td>
      <td>93.0</td>
      <td>3.65</td>
      <td>7.0</td>
      <td>0.89</td>
      <td>NaN</td>
      <td>161.0</td>
    </tr>
    <tr>
      <th>0.215</th>
      <th>0.23</th>
      <th>5.10</th>
      <td>8.000000</td>
      <td>0.041</td>
      <td>0.99688</td>
      <td>64.0</td>
      <td>3.42</td>
      <td>3.0</td>
      <td>0.44</td>
      <td>NaN</td>
      <td>157.0</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">4.4</th>
      <th>0.320</th>
      <th>0.39</th>
      <th>4.30</th>
      <td>12.800000</td>
      <td>0.030</td>
      <td>0.98904</td>
      <td>31.0</td>
      <td>3.46</td>
      <td>8.0</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>127.0</td>
    </tr>
    <tr>
      <th>0.460</th>
      <th>0.10</th>
      <th>2.80</th>
      <td>13.100000</td>
      <td>0.024</td>
      <td>0.98816</td>
      <td>31.0</td>
      <td>3.48</td>
      <td>6.0</td>
      <td>0.34</td>
      <td>NaN</td>
      <td>111.0</td>
    </tr>
    <tr>
      <th>0.540</th>
      <th>0.09</th>
      <th>5.10</th>
      <td>12.200000</td>
      <td>0.038</td>
      <td>0.99022</td>
      <td>52.0</td>
      <td>3.41</td>
      <td>7.0</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>97.0</td>
    </tr>
    <tr>
      <th>4.5</th>
      <th>0.190</th>
      <th>0.21</th>
      <th>0.95</th>
      <td>8.000000</td>
      <td>0.033</td>
      <td>0.99332</td>
      <td>89.0</td>
      <td>3.34</td>
      <td>5.0</td>
      <td>0.42</td>
      <td>NaN</td>
      <td>159.0</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">4.6</th>
      <th>0.445</th>
      <th>0.00</th>
      <th>1.40</th>
      <td>10.200000</td>
      <td>0.053</td>
      <td>0.99426</td>
      <td>11.0</td>
      <td>3.79</td>
      <td>5.0</td>
      <td>0.55</td>
      <td>NaN</td>
      <td>178.0</td>
    </tr>
    <tr>
      <th>0.520</th>
      <th>0.15</th>
      <th>2.10</th>
      <td>13.100000</td>
      <td>0.054</td>
      <td>0.99340</td>
      <td>8.0</td>
      <td>3.90</td>
      <td>4.0</td>
      <td>0.56</td>
      <td>65.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="6" valign="top">4.7</th>
      <th>0.145</th>
      <th>0.29</th>
      <th>1.00</th>
      <td>11.300000</td>
      <td>0.042</td>
      <td>0.99080</td>
      <td>35.0</td>
      <td>3.76</td>
      <td>6.0</td>
      <td>0.49</td>
      <td>NaN</td>
      <td>90.0</td>
    </tr>
    <tr>
      <th>0.335</th>
      <th>0.14</th>
      <th>1.30</th>
      <td>10.500000</td>
      <td>0.036</td>
      <td>0.99212</td>
      <td>69.0</td>
      <td>3.47</td>
      <td>5.0</td>
      <td>0.46</td>
      <td>NaN</td>
      <td>168.0</td>
    </tr>
    <tr>
      <th>0.455</th>
      <th>0.18</th>
      <th>1.90</th>
      <td>14.000000</td>
      <td>0.036</td>
      <td>0.98746</td>
      <td>33.0</td>
      <td>3.21</td>
      <td>7.0</td>
      <td>0.83</td>
      <td>NaN</td>
      <td>106.0</td>
    </tr>
    <tr>
      <th>0.600</th>
      <th>0.17</th>
      <th>2.30</th>
      <td>12.900000</td>
      <td>0.058</td>
      <td>0.99320</td>
      <td>17.0</td>
      <td>3.85</td>
      <td>6.0</td>
      <td>0.60</td>
      <td>106.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.670</th>
      <th>0.09</th>
      <th>1.00</th>
      <td>13.600000</td>
      <td>0.020</td>
      <td>0.98722</td>
      <td>5.0</td>
      <td>3.30</td>
      <td>5.0</td>
      <td>0.34</td>
      <td>NaN</td>
      <td>9.0</td>
    </tr>
    <tr>
      <th>0.785</th>
      <th>0.00</th>
      <th>3.40</th>
      <td>13.800000</td>
      <td>0.036</td>
      <td>0.98981</td>
      <td>23.0</td>
      <td>3.53</td>
      <td>6.0</td>
      <td>0.92</td>
      <td>NaN</td>
      <td>134.0</td>
    </tr>
    <tr>
      <th rowspan="9" valign="top">4.8</th>
      <th>0.130</th>
      <th>0.32</th>
      <th>1.20</th>
      <td>11.800000</td>
      <td>0.042</td>
      <td>0.98980</td>
      <td>40.0</td>
      <td>3.42</td>
      <td>7.0</td>
      <td>0.64</td>
      <td>NaN</td>
      <td>98.0</td>
    </tr>
    <tr>
      <th>0.170</th>
      <th>0.28</th>
      <th>2.90</th>
      <td>11.300000</td>
      <td>0.030</td>
      <td>0.99020</td>
      <td>22.0</td>
      <td>3.38</td>
      <td>7.0</td>
      <td>0.34</td>
      <td>NaN</td>
      <td>111.0</td>
    </tr>
    <tr>
      <th>0.210</th>
      <th>0.21</th>
      <th>10.20</th>
      <td>12.200000</td>
      <td>0.037</td>
      <td>0.99324</td>
      <td>17.0</td>
      <td>3.66</td>
      <td>7.0</td>
      <td>0.48</td>
      <td>NaN</td>
      <td>112.0</td>
    </tr>
    <tr>
      <th>0.225</th>
      <th>0.38</th>
      <th>1.20</th>
      <td>10.300000</td>
      <td>0.074</td>
      <td>0.99132</td>
      <td>47.0</td>
      <td>3.31</td>
      <td>6.0</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>130.0</td>
    </tr>
    <tr>
      <th>0.260</th>
      <th>0.23</th>
      <th>10.60</th>
      <td>11.500000</td>
      <td>0.034</td>
      <td>0.99274</td>
      <td>23.0</td>
      <td>3.46</td>
      <td>7.0</td>
      <td>0.28</td>
      <td>NaN</td>
      <td>111.0</td>
    </tr>
    <tr>
      <th>0.290</th>
      <th>0.23</th>
      <th>1.10</th>
      <td>11.900000</td>
      <td>0.044</td>
      <td>0.98924</td>
      <td>38.0</td>
      <td>3.28</td>
      <td>6.0</td>
      <td>0.34</td>
      <td>NaN</td>
      <td>180.0</td>
    </tr>
    <tr>
      <th>0.330</th>
      <th>0.00</th>
      <th>6.50</th>
      <td>9.900000</td>
      <td>0.028</td>
      <td>0.99370</td>
      <td>34.0</td>
      <td>3.35</td>
      <td>5.0</td>
      <td>0.61</td>
      <td>NaN</td>
      <td>163.0</td>
    </tr>
    <tr>
      <th>0.340</th>
      <th>0.00</th>
      <th>6.50</th>
      <td>9.900000</td>
      <td>0.028</td>
      <td>0.99390</td>
      <td>33.0</td>
      <td>3.36</td>
      <td>6.0</td>
      <td>0.61</td>
      <td>NaN</td>
      <td>163.0</td>
    </tr>
    <tr>
      <th>0.650</th>
      <th>0.12</th>
      <th>1.10</th>
      <td>13.500000</td>
      <td>0.013</td>
      <td>0.99246</td>
      <td>4.0</td>
      <td>3.32</td>
      <td>4.0</td>
      <td>0.36</td>
      <td>NaN</td>
      <td>10.0</td>
    </tr>
    <tr>
      <th rowspan="5" valign="top">4.9</th>
      <th>0.235</th>
      <th>0.27</th>
      <th>11.75</th>
      <td>9.400000</td>
      <td>0.030</td>
      <td>0.99540</td>
      <td>34.0</td>
      <td>3.07</td>
      <td>6.0</td>
      <td>0.50</td>
      <td>NaN</td>
      <td>118.0</td>
    </tr>
    <tr>
      <th>0.330</th>
      <th>0.31</th>
      <th>1.20</th>
      <td>14.000000</td>
      <td>0.016</td>
      <td>0.98713</td>
      <td>39.0</td>
      <td>3.33</td>
      <td>8.0</td>
      <td>0.59</td>
      <td>NaN</td>
      <td>150.0</td>
    </tr>
    <tr>
      <th>0.335</th>
      <th>0.14</th>
      <th>1.30</th>
      <td>10.466667</td>
      <td>0.036</td>
      <td>0.99212</td>
      <td>69.0</td>
      <td>3.47</td>
      <td>5.0</td>
      <td>0.46</td>
      <td>NaN</td>
      <td>168.0</td>
    </tr>
    <tr>
      <th>0.345</th>
      <th>0.34</th>
      <th>1.00</th>
      <td>10.100000</td>
      <td>0.068</td>
      <td>0.99138</td>
      <td>32.0</td>
      <td>3.24</td>
      <td>5.0</td>
      <td>0.40</td>
      <td>NaN</td>
      <td>143.0</td>
    </tr>
    <tr>
      <th>0.420</th>
      <th>0.00</th>
      <th>2.10</th>
      <td>14.000000</td>
      <td>0.048</td>
      <td>0.99154</td>
      <td>16.0</td>
      <td>3.71</td>
      <td>7.0</td>
      <td>0.74</td>
      <td>42.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>...</th>
      <th>...</th>
      <th>...</th>
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
    </tr>
    <tr>
      <th rowspan="3" valign="top">12.6</th>
      <th>0.380</th>
      <th>0.66</th>
      <th>2.60</th>
      <td>9.800000</td>
      <td>0.088</td>
      <td>1.00100</td>
      <td>10.0</td>
      <td>3.17</td>
      <td>6.0</td>
      <td>0.68</td>
      <td>41.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.390</th>
      <th>0.49</th>
      <th>2.50</th>
      <td>10.300000</td>
      <td>0.080</td>
      <td>0.99920</td>
      <td>8.0</td>
      <td>3.07</td>
      <td>6.0</td>
      <td>0.82</td>
      <td>20.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.410</th>
      <th>0.54</th>
      <th>2.80</th>
      <td>11.300000</td>
      <td>0.103</td>
      <td>0.99939</td>
      <td>19.0</td>
      <td>3.21</td>
      <td>6.0</td>
      <td>0.76</td>
      <td>41.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">12.7</th>
      <th>0.590</th>
      <th>0.45</th>
      <th>2.30</th>
      <td>9.300000</td>
      <td>0.082</td>
      <td>1.00000</td>
      <td>11.0</td>
      <td>3.00</td>
      <td>6.0</td>
      <td>0.70</td>
      <td>22.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">0.600</th>
      <th>0.49</th>
      <th>2.80</th>
      <td>11.400000</td>
      <td>0.075</td>
      <td>0.99940</td>
      <td>5.0</td>
      <td>3.14</td>
      <td>5.0</td>
      <td>0.57</td>
      <td>19.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.65</th>
      <th>2.30</th>
      <td>9.900000</td>
      <td>0.063</td>
      <td>0.99970</td>
      <td>6.0</td>
      <td>3.03</td>
      <td>5.0</td>
      <td>0.57</td>
      <td>25.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">12.8</th>
      <th>0.300</th>
      <th>0.74</th>
      <th>2.60</th>
      <td>10.800000</td>
      <td>0.095</td>
      <td>0.99940</td>
      <td>9.0</td>
      <td>3.20</td>
      <td>7.0</td>
      <td>0.77</td>
      <td>28.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.615</th>
      <th>0.66</th>
      <th>5.80</th>
      <td>10.000000</td>
      <td>0.083</td>
      <td>1.00220</td>
      <td>7.0</td>
      <td>3.07</td>
      <td>7.0</td>
      <td>0.73</td>
      <td>42.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.840</th>
      <th>0.63</th>
      <th>2.40</th>
      <td>10.400000</td>
      <td>0.088</td>
      <td>0.99970</td>
      <td>13.0</td>
      <td>3.10</td>
      <td>6.0</td>
      <td>0.60</td>
      <td>35.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">12.9</th>
      <th>0.350</th>
      <th>0.49</th>
      <th>5.80</th>
      <td>12.000000</td>
      <td>0.066</td>
      <td>1.00140</td>
      <td>5.0</td>
      <td>3.20</td>
      <td>7.0</td>
      <td>0.66</td>
      <td>35.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.500</th>
      <th>0.55</th>
      <th>2.80</th>
      <td>10.900000</td>
      <td>0.072</td>
      <td>1.00012</td>
      <td>7.0</td>
      <td>3.09</td>
      <td>6.0</td>
      <td>0.68</td>
      <td>24.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">13.0</th>
      <th>0.320</th>
      <th>0.65</th>
      <th>2.60</th>
      <td>10.600000</td>
      <td>0.093</td>
      <td>0.99960</td>
      <td>15.0</td>
      <td>3.05</td>
      <td>5.0</td>
      <td>0.61</td>
      <td>47.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.470</th>
      <th>0.49</th>
      <th>4.30</th>
      <td>12.700000</td>
      <td>0.085</td>
      <td>1.00210</td>
      <td>6.0</td>
      <td>3.30</td>
      <td>6.0</td>
      <td>0.68</td>
      <td>47.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">13.2</th>
      <th>0.380</th>
      <th>0.55</th>
      <th>2.70</th>
      <td>9.400000</td>
      <td>0.081</td>
      <td>1.00060</td>
      <td>5.0</td>
      <td>2.98</td>
      <td>5.0</td>
      <td>0.54</td>
      <td>16.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.460</th>
      <th>0.52</th>
      <th>2.20</th>
      <td>9.000000</td>
      <td>0.071</td>
      <td>1.00060</td>
      <td>12.0</td>
      <td>3.10</td>
      <td>6.0</td>
      <td>0.56</td>
      <td>35.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="3" valign="top">13.3</th>
      <th>0.290</th>
      <th>0.75</th>
      <th>2.80</th>
      <td>11.400000</td>
      <td>0.084</td>
      <td>0.99860</td>
      <td>23.0</td>
      <td>3.04</td>
      <td>7.0</td>
      <td>0.68</td>
      <td>43.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.340</th>
      <th>0.52</th>
      <th>3.20</th>
      <td>9.500000</td>
      <td>0.094</td>
      <td>1.00140</td>
      <td>17.0</td>
      <td>3.05</td>
      <td>6.0</td>
      <td>0.81</td>
      <td>53.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.430</th>
      <th>0.58</th>
      <th>1.90</th>
      <td>9.000000</td>
      <td>0.070</td>
      <td>1.00040</td>
      <td>15.0</td>
      <td>3.06</td>
      <td>5.0</td>
      <td>0.49</td>
      <td>40.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13.4</th>
      <th>0.270</th>
      <th>0.62</th>
      <th>2.60</th>
      <td>9.700000</td>
      <td>0.082</td>
      <td>1.00020</td>
      <td>6.0</td>
      <td>3.16</td>
      <td>6.0</td>
      <td>0.67</td>
      <td>21.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13.5</th>
      <th>0.530</th>
      <th>0.79</th>
      <th>4.80</th>
      <td>13.000000</td>
      <td>0.120</td>
      <td>1.00180</td>
      <td>23.0</td>
      <td>3.18</td>
      <td>5.0</td>
      <td>0.77</td>
      <td>77.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13.7</th>
      <th>0.415</th>
      <th>0.68</th>
      <th>2.90</th>
      <td>10.000000</td>
      <td>0.085</td>
      <td>1.00140</td>
      <td>17.0</td>
      <td>3.06</td>
      <td>6.0</td>
      <td>0.80</td>
      <td>43.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>13.8</th>
      <th>0.490</th>
      <th>0.67</th>
      <th>3.00</th>
      <td>12.000000</td>
      <td>0.093</td>
      <td>0.99860</td>
      <td>6.0</td>
      <td>3.02</td>
      <td>6.0</td>
      <td>0.93</td>
      <td>15.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14.0</th>
      <th>0.410</th>
      <th>0.63</th>
      <th>3.80</th>
      <td>10.800000</td>
      <td>0.089</td>
      <td>1.00140</td>
      <td>6.0</td>
      <td>3.01</td>
      <td>6.0</td>
      <td>0.81</td>
      <td>47.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>14.2</th>
      <th>0.270</th>
      <th>0.49</th>
      <th>1.10</th>
      <td>11.100000</td>
      <td>0.037</td>
      <td>0.99200</td>
      <td>33.0</td>
      <td>3.15</td>
      <td>6.0</td>
      <td>0.54</td>
      <td>NaN</td>
      <td>156.0</td>
    </tr>
    <tr>
      <th>14.3</th>
      <th>0.310</th>
      <th>0.74</th>
      <th>1.80</th>
      <td>8.400000</td>
      <td>0.075</td>
      <td>1.00080</td>
      <td>6.0</td>
      <td>2.86</td>
      <td>6.0</td>
      <td>0.79</td>
      <td>15.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15.0</th>
      <th>0.210</th>
      <th>0.44</th>
      <th>2.20</th>
      <td>9.200000</td>
      <td>0.075</td>
      <td>1.00005</td>
      <td>10.0</td>
      <td>3.07</td>
      <td>7.0</td>
      <td>0.84</td>
      <td>24.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15.5</th>
      <th>0.645</th>
      <th>0.49</th>
      <th>4.20</th>
      <td>11.100000</td>
      <td>0.095</td>
      <td>1.00315</td>
      <td>10.0</td>
      <td>2.92</td>
      <td>5.0</td>
      <td>0.74</td>
      <td>23.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th rowspan="2" valign="top">15.6</th>
      <th>0.645</th>
      <th>0.49</th>
      <th>4.20</th>
      <td>11.100000</td>
      <td>0.095</td>
      <td>1.00315</td>
      <td>10.0</td>
      <td>2.92</td>
      <td>5.0</td>
      <td>0.74</td>
      <td>23.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>0.685</th>
      <th>0.76</th>
      <th>3.70</th>
      <td>11.200000</td>
      <td>0.100</td>
      <td>1.00320</td>
      <td>6.0</td>
      <td>2.95</td>
      <td>7.0</td>
      <td>0.68</td>
      <td>43.0</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>15.9</th>
      <th>0.360</th>
      <th>0.65</th>
      <th>7.50</th>
      <td>14.900000</td>
      <td>0.096</td>
      <td>0.99760</td>
      <td>22.0</td>
      <td>2.98</td>
      <td>5.0</td>
      <td>0.84</td>
      <td>71.0</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>5288 rows × 9 columns</p>
</div>




```python
#save changes to the next section
df.to_csv('winequality-edited.csv',index=False)
```


```python
df.shape[0]
```




    6497



# conclusions using query method of pandas 
example of query --> df_m = df.query('diagnosis == "M"')
                     
                     df_a = df.query('income == " >50K"')  

## do wines with higher alcoholic content receive better ratings?


```python
# getting the median amount of alcohol content
alcohol_median = df['alcohol'].median()
alcohol_median
```




    10.3




```python
# select samples with alcohol content less than the median 

low_alcohol = df.query('alcohol < 10.3')
low_alcohol['quality'].count()

```




    3177




```python
high_alcohol = df.query('alcohol >= 10.3')
high_alcohol['quality'].count()
```




    3320




```python
low_alcohol = df.query('alcohol < 10.3')
high_alcohol = df.query('alcohol >= 10.3')
num_samples = df.shape[0]
num_samples == low_alcohol['quality'].count() + high_alcohol['quality'].count()
```




    True




```python
# get mean quality rating for the low alcohol and high alcohol groups
low_alco_quality = low_alcohol['quality'].mean()
low_alco_quality
```




    5.475920679886686




```python
high_alco_quality = high_alcohol['quality'].mean()
high_alco_quality
```




    6.146084337349397



### So we can say that higher alcohol content receive better ratings

## Do sweeter wines receive better rating ?


```python
# get median amount of residual sugar
df['residual_sugar'].median()
```




    3.0




```python
# select samples with residual sugar less than the median
low_sugar = df.query('residual_sugar < 3.0')

# select samples with residual sugar greater than or equal to the median
high_sugar = df.query('residual_sugar >= 3.0')

# ensure these queries included each sample exactly once
num_samples == low_sugar['quality'].count() + high_sugar['quality'].count() # should be True
```




    True




```python
# get mean quality rating for the low sugar and high sugar groups
low_sugar['quality'].mean()
```




    5.808800743724822




```python
high_sugar['quality'].mean()
```




    5.82782874617737



### so we can say that sweeter wines receive better ratings 

# Plotting with Matplotlib

### #1 Do wines with higher alcohol content receive better ratings ?


```python
# Use query to select each group and get its mean quality
median = df['alcohol'].median()
low = df.query('alcohol < {}'.format(median))
high = df.query('alcohol >= {}'.format(median))

```


```python
mean_quality_low = low['quality'].mean()
mean_quality_high = high['quality'].mean()
```


```python
#create a bar chart
location = [1,2]
heights = [mean_quality_low,mean_quality_high]
labels = ['Low','High']
plt.bar(location,heights,tick_label=labels,color='g')
plt.title('Average Quality Ratings by Alcohol Content')
plt.xlabel('Alcohol Content')
plt.ylabel('Average Quality Rating');
```


![png](case_files/case_64_0.png)


### #2 Do Sweeter wines receive higher ratings?


```python
meadian = df['residual_sugar'].median()
low = df.query('residual_sugar < {}'.format(median))
high = df.query('residual_sugar >= {}'.format(median))
```


```python
sugar_mean_lowquality = low['quality'].mean()
sugar_mean_highquality = high['quality'].mean()
```


```python
#create a bar graph
location = [1,2]
heights =[sugar_mean_lowquality,sugar_mean_highquality]
labels = ['low','high']
plt.bar(location,heights,tick_label=labels,color='orange')
plt.title('Average Quality Ratings by residual Content')
plt.xlabel('residual sugar Content')
plt.ylabel('Average Quality Rating');
```


![png](case_files/case_68_0.png)


### #3: What level of acidity receives the highest average rating?


```python
fa_mean = df.groupby('fixed_acidity')['quality'].mean()
fa = fa_mean.mean()
fa
```




    5.828059057495961




```python
va_mean = df.groupby('volatile_acidity')['quality'].mean()
va = va_mean.mean()
va
```




    5.442571682876287




```python
rs_mean = df.groupby('residual_sugar')['quality'].mean()
rs = rs_mean.mean()
rs
```




    5.808154369129453




```python
ca_mean = df.groupby('citric_acid')['quality'].mean()
ca = ca_mean.mean()
ca
```




    5.662165056090447




```python
# Create a bar chart with proper labels
heights = [fa,va,rs,ca]
labels = ['fixed_acidity', 'volatile_acidity', 'residual_sugar','ca_mean']
plt.bar([1,2,3,4],heights,tick_label=labels,color='red')
plt.title('Bar chart for all four acidity level')
plt.xlabel('acidity levels')
plt.ylabel('mean quality')
```




    Text(0,0.5,'mean quality')




![png](case_files/case_74_1.png)



```python
heights = [fa,va,rs,ca]
plt.plot([1,2,3,4],heights,linestyle='solid',color='r')

```




    [<matplotlib.lines.Line2D at 0x1e6b4af1eb8>]




![png](case_files/case_75_1.png)


# Type and Quality Plot with Matplotlib


```python
import seaborn as sns
sns.set_style('darkgrid')


```


```python
# get counts for each rating and color
red_color_counts = df.groupby(['color_red','quality']).count()['pH']
red_color_counts
```




    color_red  quality
    red        3           10
               4           53
               5          681
               6          638
               7          199
               8           18
    Name: pH, dtype: int64




```python
white_color_counts = df.groupby(['color_white','quality']).count()['pH']
white_color_counts
```




    color_white  quality
    white        3            20
                 4           163
                 5          1457
                 6          2198
                 7           880
                 8           175
                 9             5
    Name: pH, dtype: int64




```python
# get total counts for each color
color_total_r =df.groupby('color_red').count()['pH']
color_total_r
```




    color_red
    red    1599
    Name: pH, dtype: int64




```python
color_total_w =df.groupby('color_white').count()['pH']
color_total_w
```




    color_white
    white    4898
    Name: pH, dtype: int64




```python
# get proportions by dividing red rating counts by total # of red samples
red_proportion = red_color_counts['red'] / color_total_r['red']
red_proportion
```




    quality
    3    0.006254
    4    0.033146
    5    0.425891
    6    0.398999
    7    0.124453
    8    0.011257
    Name: pH, dtype: float64



#### since the index is upto 8 we have to create a new row as 9 which value is 0


```python
red_proportion['9'] = 0
red_proportion
```




    quality
    3    0.006254
    4    0.033146
    5    0.425891
    6    0.398999
    7    0.124453
    8    0.011257
    9    0.000000
    Name: pH, dtype: float64




```python
white_proportion = white_color_counts['white'] / color_total_w['white']
white_proportion
```




    quality
    3    0.004083
    4    0.033279
    5    0.297468
    6    0.448755
    7    0.179665
    8    0.035729
    9    0.001021
    Name: pH, dtype: float64



### Plot proportions on a bar chart
Set the x coordinate location for each rating group and and width of each bar.


```python
ind = np.arange(len(red_proportion))  # the x locations for the groups
width = 0.35   
```


```python
# plot bars
red_bars = plt.bar(ind,red_proportion, width, color='r', alpha=.7, label='Red Wine')
white_bars = plt.bar(ind + width, white_proportion, width, color='w', alpha=.7, label='White Wine')

# title and labels
plt.ylabel('Proportion')
plt.xlabel('Quality')
plt.title('Proportion by Wine Color and Quality')
locations = ind + width / 2  # xtick locations
labels = ['3', '4', '5', '6', '7', '8', '9']  # xtick labels
plt.xticks(locations, labels)

# legend
plt.legend()

```




    <matplotlib.legend.Legend at 0x1e6a50616d8>




![png](case_files/case_88_1.png)



```python
nbconvert -f blogger-html Case study 1 - detecting red and white wine quality.ipynb
```


      File "<ipython-input-1-d8ccd1830a2f>", line 1
        nbconvert -f blogger-html Case study 1 - detecting red and white wine quality.ipynb
                           ^
    SyntaxError: invalid syntax
    

