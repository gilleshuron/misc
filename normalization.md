
# JSON Lines normalization


```python
import pandas as pd
from pandas.io.json import json_normalize

i1='["h1","h2"]'+"\n"+'[1,"12"]'

i2='{"h1":1,"h2":"12"}'+'\n'+'{"h1":2,"h2":"24"}'

i3='{"h1":1,"h2":{"h21":"12","h22":12}}'+'\n'
i3+='{"h1":2,"h2":{"h21":"24","h22":24}}'+'\n'
i3+='{"h1":3,"h2":{"h21":"28","h22":28,"h23":16}}'

```


```python
pd.read_json(i2, lines='true')
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
      <th>h1</th>
      <th>h2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>24</td>
    </tr>
  </tbody>
</table>
</div>




```python
pd.read_json(i2, lines='true')

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
      <th>h1</th>
      <th>h2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>12</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>24</td>
    </tr>
  </tbody>
</table>
</div>




```python
d=pd.read_json(i3, lines='true')
d
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
      <th>h1</th>
      <th>h2</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>1</td>
      <td>{'h21': '12', 'h22': 12}</td>
    </tr>
    <tr>
      <th>1</th>
      <td>2</td>
      <td>{'h21': '24', 'h22': 24}</td>
    </tr>
    <tr>
      <th>2</th>
      <td>3</td>
      <td>{'h21': '28', 'h22': 28, 'h23': 16}</td>
    </tr>
  </tbody>
</table>
</div>




```python
json_normalize(d['h2'])
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
      <th>h21</th>
      <th>h22</th>
      <th>h23</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>12</td>
      <td>12</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1</th>
      <td>24</td>
      <td>24</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>2</th>
      <td>28</td>
      <td>28</td>
      <td>16.0</td>
    </tr>
  </tbody>
</table>
</div>




```python

```
