
## Pandas Data Munging Data Wrangling

#### Encoding Problem
Try using 'ISO-8859-1' if there is 'utf-8' error.

    df = pd.read_csv('file.csv', sep=',', quotechar='"', enconding='ISO-8859-1')


```python
import pandas as pd
import numpy as np
```

#### Create DataFrame from dictionary of ndarrays / lists


```python
d1 = {'one' : [1., 2., 3., 4.], 'two' : ['4', '3', '2', '1']}
df1 = pd.DataFrame(d1)
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



#### Convert string to numeric.
Or using 

    df1['two] = df1['two'].astype(float)
    df1['two] = df1['two'].astype(np.int64)


```python
df1['two'] = pd.to_numeric(df1['two'], errors='coerce')
df1
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>one</th>
      <th>two</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1.0</td>
      <td>4</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2.0</td>
      <td>3</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3.0</td>
      <td>2</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
      <td>1</td>
    </tr>
  </tbody>
</table>
</div>



#### Convert String to Datetime

    df['col'] = pd.to_datetime(df['col'], format="%m/%d/%Y %H:%M:%S")

#### Creat DataFrame From a list of dicts


```python
d2 = [{'a': 1, 'b': 2}, {'a': 5, 'b': 10, 'c': 20}]
df2 = pd.DataFrame(d2)
df2
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>a</th>
      <th>b</th>
      <th>c</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>5</td>
      <td>10</td>
      <td>20.0</td>
    </tr>
  </tbody>
</table>
</div>



#### Create DataFrame From list


```python
a = [1,2,3,4,2,2,5]
df = pd.DataFrame(a, columns=['new'])
```

#### Adding new column


```python
b = [2,3,4,5,6,6]
df['add'] = pd.DataFrame(b)
```

#### Create new column by doing math about existing ones


```python
df['sub'] = df['add'] - df['new']
```

#### Check column names


```python
df.columns
```




    Index(['new', 'add', 'sub'], dtype='object')



#### Check unique values of column


```python
df.new.unique()
```




    array([1, 2, 3, 4, 5])



#### Group by and count the number


```python
df.groupby('new').count()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>add</th>
      <th>sub</th>
    </tr>
    <tr>
      <th>new</th>
      <th></th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>3</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>4</th>
      <td>1</td>
      <td>1</td>
    </tr>
    <tr>
      <th>5</th>
      <td>0</td>
      <td>0</td>
    </tr>
  </tbody>
</table>
</div>



#### Reset index


```python
df.reset_index()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>index</th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>5</td>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>6</td>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



#### Group by 'column1' and get the sum for 'column2'
    df.groupby('column1').agg({'column2':sum, 'column3':mean})


```python
df[['new','add']].groupby('new').sum()
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>add</th>
    </tr>
    <tr>
      <th>new</th>
      <th></th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>1</th>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>15.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>5.0</td>
    </tr>
    <tr>
      <th>5</th>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



#### Check the NULL number and not NULL number for 'column1'


```python
df.isnull().sum()
```




    new    0
    add    1
    sub    1
    dtype: int64




```python
df.notnull().sum().tolist()
```




    [7, 6, 6]



#### Check Duplicates


```python
df.duplicated().tolist()
```




    [False, False, False, False, False, True, False]




```python
df.drop_duplicates(inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>



#### Adding new column by mapping


```python
df['large3'] = df['new'].map(lambda x: True if x >=3 else False)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



#### Sort by column values


```python
df.sort_values(by='new', ascending=False)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
  </tbody>
</table>
</div>



#### Sort dataframe by multiple columns

    df = df.sort(['col1','col2','col3'],ascending=[1,1,0])

#### Fill in NaN

    df.fillna(0, inplace=True)


```python
df.fillna({'add':0,'sub':-1}, inplace=True)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>-1.0</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



#### NaN vs None

    NaN is a numeric value. None is an internal Python type (NoneType)
    NaN can be used as a numerical value on mathematical operations, while None cannot (or at least shouldn't).

##### Pandas Axis

    axis=0 along the rows (namely, index in pandas), and axis=1 along the columns.

#### Set Value for some cell


```python
df.set_value(6, 'sub', 0)
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>



#### map function with a function as parameter 
    using lambda function
    change for this column


```python
def f_t(x):
    return x**2

df['square'] = df['new'].map(lambda x:f_t(x))
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
      <th>square</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>4</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>16</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
      <td>4</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>True</td>
      <td>25</td>
    </tr>
  </tbody>
</table>
</div>



#### Selection with two conditions
    Note the "()" and "&"


```python
print (df[(df['new']==2) & (df['sub']==1)]['square'])
```

    1    4
    Name: square, dtype: int64


#### using loc for change values

    df.loc[(df['column1'] == some_value) & (df['column2'] == some_other_value), ['column_to_change']] = new_value
Note: using '[]' instead of '()'


```python
df.loc[(df['new']==2) & (df['sub']==4),['square']] = 36
df.loc[df['new'].notnull(), ['square']] = df['new']**2 / 2
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
      <th>square</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>4.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>True</td>
      <td>12.5</td>
    </tr>
  </tbody>
</table>
</div>



#### Add new column to DataFrame.
    df.assign(columnname=Series/Scalar/Array)
Note: Need to assign again, otherwise it did not change the original one.
    
Or:

    df = df.assign(test=df['new']**3)


```python
temp = df['new']**3
df = df.assign(cube=temp)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
      <th>square</th>
      <th>cube</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>0.5</td>
      <td>1</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>2.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>4.5</td>
      <td>27</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>8.0</td>
      <td>64</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
      <td>2.0</td>
      <td>8</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>True</td>
      <td>12.5</td>
      <td>125</td>
    </tr>
  </tbody>
</table>
</div>



#### Delete Column
    df.drop('columname', axis=1, inplace=True)
Or, using 'del'

    del df['cube']
Or, using "pop()"

    df.pop('cube')


```python
df.drop('cube', axis=1, inplace=True)
df
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
      <th>square</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>4.5</td>
    </tr>
    <tr>
      <th>3</th>
      <td>4</td>
      <td>5.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>8.0</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>6</th>
      <td>5</td>
      <td>0.0</td>
      <td>0.0</td>
      <td>True</td>
      <td>12.5</td>
    </tr>
  </tbody>
</table>
</div>



#### Select row according to values.


```python
df[df['new'].isin([1,2,3])]
```




<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>new</th>
      <th>add</th>
      <th>sub</th>
      <th>large3</th>
      <th>square</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>2.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>0.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>3.0</td>
      <td>1.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>4.0</td>
      <td>1.0</td>
      <td>True</td>
      <td>4.5</td>
    </tr>
    <tr>
      <th>4</th>
      <td>2</td>
      <td>6.0</td>
      <td>4.0</td>
      <td>False</td>
      <td>2.0</td>
    </tr>
  </tbody>
</table>
</div>



#### Set Index
     df.index = df['date']
