## Введение
Добро пожаловать! Сегодня мы разберем некоторые вопросы и задания, которые позволяют определить на собеседовании, знаете ли вы на начальном уровне язык программирования
Python. Вы можете самостоятельно пройти все эти задания. Для этого вам необходимо скачать архив из репозитория [USA университеты][1] <br>

Вам нужен файл cc_institution_grads. Список заданий представлен ниже:

- Напечатайте данный лист в обратном порядке 
    `my_list=[1,2,3,4,5]`
- Считайте данные из файла cc_institution_grads.csv в переменную df
- Какие гендеры есть в данной таблице? Выведите все
- Выведите топ 5 лет, которые встречаются в БД (Используя groupby, и как сделать без него)
- Выведите топ 5 рас, встречающихся среди Женщин.
- Есть база данных. используя ее, найдите среднее значение возраста, и максимальное.
    `db2 = sns.load_dataset('titanic')`
- Укажите процент выживших в аварии
- Создайте таблицу, в которой будет указано: минимальный возраст каждого пола, максимальный возраст каждого пола
- Найдите, в каком классе мест пассажиров разница возрастов между самым старшим и самым младшим максимальна.
- Есть два датафрейма. Объедините их с помощью Left join метода (то есть чтобы все значения из левой таблицы остались, даже если у правой таблицы нет значений для каких-то наименований)
    ```python
    df1 = pd.DataFrame({'lkey': ['rabbit', 'wolf', 'parrot', 'rabbit','rabbit', 'wolf', 'parrot', 'rabbit','elephant'],
                        'kg': [1.2, 12.6, 0.4, 1.8,1.9, 11.1, 0.2, 1.6,340.4]})
    df2 = pd.DataFrame({'rkey': ['rabbit', 'wolf', 'parrot','dolphin'],
                        'diet': ['carrot', 'meat', 'seeds','fish']})
    ```

Пройдя эти задания, проверяющему вы покажете, что вы:

- [x] Умеете работать с БД
- [x] Умеете использовать `.groupby` `.agg` `.merge` `.unique` `Counter` `reversed`
> Я обнаружил для себя, что еще плохо знаю язык Markdown, поэтому вот [статья][2] по написанию отличных файлов README

[1]:https://github.com/Enoki-ru/USA-Universities. "Мой личный репозиторий"
[2]:https://skillbox.ru/media/code/yazyk-razmetki-markdown-shpargalka-po-sintaksisu-s-primerami/  "Ссылка на SkillBox"


```python
# Напечатайте лист в обратном порядке
```


```python
my_list=[1,2,3,4,5]
```


```python
#Метод 1
print(my_list[::-1])
#Метод 2
q=list(reversed(my_list))
print(q)
```

    [5, 4, 3, 2, 1]
    [5, 4, 3, 2, 1]
    


```python
#считайте данные из файла cc_institution_grads.csv в переменную df
```


```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
df=pd.read_csv("cc_institution_grads.csv", sep=',')
df
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
      <th>index</th>
      <th>unitid</th>
      <th>year</th>
      <th>gender</th>
      <th>race</th>
      <th>cohort</th>
      <th>grad_cohort</th>
      <th>grad_100</th>
      <th>grad_150</th>
      <th>grad_100_rate</th>
      <th>grad_150_rate</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>100760</td>
      <td>2011</td>
      <td>B</td>
      <td>X</td>
      <td>2y all</td>
      <td>446.0</td>
      <td>73.0</td>
      <td>105.0</td>
      <td>16.4</td>
      <td>23.5</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>100760</td>
      <td>2011</td>
      <td>M</td>
      <td>X</td>
      <td>2y all</td>
      <td>185.0</td>
      <td>NaN</td>
      <td>40.0</td>
      <td>NaN</td>
      <td>21.6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>2</td>
      <td>100760</td>
      <td>2011</td>
      <td>F</td>
      <td>X</td>
      <td>2y all</td>
      <td>261.0</td>
      <td>NaN</td>
      <td>65.0</td>
      <td>NaN</td>
      <td>24.9</td>
    </tr>
    <tr>
      <th>3</th>
      <td>3</td>
      <td>100760</td>
      <td>2011</td>
      <td>B</td>
      <td>W</td>
      <td>2y all</td>
      <td>348.0</td>
      <td>NaN</td>
      <td>86.0</td>
      <td>NaN</td>
      <td>24.7</td>
    </tr>
    <tr>
      <th>4</th>
      <td>4</td>
      <td>100760</td>
      <td>2011</td>
      <td>M</td>
      <td>W</td>
      <td>2y all</td>
      <td>162.0</td>
      <td>NaN</td>
      <td>35.0</td>
      <td>NaN</td>
      <td>21.6</td>
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
    </tr>
    <tr>
      <th>1302097</th>
      <td>1302097</td>
      <td>168591</td>
      <td>2002</td>
      <td>F</td>
      <td>Ai</td>
      <td>4y other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1302098</th>
      <td>1302098</td>
      <td>168740</td>
      <td>2002</td>
      <td>F</td>
      <td>Ai</td>
      <td>4y other</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1302099</th>
      <td>1302099</td>
      <td>169716</td>
      <td>2002</td>
      <td>F</td>
      <td>Ai</td>
      <td>4y other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1302100</th>
      <td>1302100</td>
      <td>170082</td>
      <td>2002</td>
      <td>F</td>
      <td>Ai</td>
      <td>4y other</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
    <tr>
      <th>1302101</th>
      <td>1302101</td>
      <td>170091</td>
      <td>2002</td>
      <td>F</td>
      <td>Ai</td>
      <td>4y other</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>0.0</td>
      <td>NaN</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
<p>1302102 rows × 11 columns</p>
</div>




```python
#Какие гендеры есть в данной таблице
```


```python
#Метод 1
print(list(set(df.gender)))
#Метод 2
print(df.gender.unique())
```

    ['B', 'F', 'M']
    ['B' 'M' 'F']
    


```python
#выведите топ 5 лет, которые встречаются в БД 
```


```python
#Метод 1
from collections import Counter
count5=Counter(df['year'])
count5=count5.most_common(5)
for i in range (5):
    print(count5[i][0])
print('---------------')
#Метод 2
df.groupby('year', as_index=False) \
    .agg({'index':'count'}) \
    .sort_values(by='year', ascending=False) \
    .head(5)
```

    2011
    2012
    2013
    2010
    2009
    ---------------
    




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
      <th>year</th>
      <th>index</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>11</th>
      <td>2013</td>
      <td>110466</td>
    </tr>
    <tr>
      <th>10</th>
      <td>2012</td>
      <td>110466</td>
    </tr>
    <tr>
      <th>9</th>
      <td>2011</td>
      <td>110466</td>
    </tr>
    <tr>
      <th>8</th>
      <td>2010</td>
      <td>107856</td>
    </tr>
    <tr>
      <th>7</th>
      <td>2009</td>
      <td>107856</td>
    </tr>
  </tbody>
</table>
</div>




```python
#выведите топ 5 рас, встречающихся среди Женщин.
```


```python
df[df.gender=='F'].groupby('race', as_index=False) \
    .agg({'gender':'count'}) \
    .sort_values(by='gender', ascending=False) \
    .head(5)

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
      <th>race</th>
      <th>gender</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>A</td>
      <td>72339</td>
    </tr>
    <tr>
      <th>1</th>
      <td>Ai</td>
      <td>72339</td>
    </tr>
    <tr>
      <th>2</th>
      <td>B</td>
      <td>72339</td>
    </tr>
    <tr>
      <th>3</th>
      <td>H</td>
      <td>72339</td>
    </tr>
    <tr>
      <th>4</th>
      <td>W</td>
      <td>72339</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Есть база данных. используя ее, найдите среднее значение возраста, и максимальное.
db2 = sns.load_dataset('titanic')
db2.head()

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
      <th>survived</th>
      <th>pclass</th>
      <th>sex</th>
      <th>age</th>
      <th>sibsp</th>
      <th>parch</th>
      <th>fare</th>
      <th>embarked</th>
      <th>class</th>
      <th>who</th>
      <th>adult_male</th>
      <th>deck</th>
      <th>embark_town</th>
      <th>alive</th>
      <th>alone</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>22.0</td>
      <td>1</td>
      <td>0</td>
      <td>7.2500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>False</td>
    </tr>
    <tr>
      <th>1</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>38.0</td>
      <td>1</td>
      <td>0</td>
      <td>71.2833</td>
      <td>C</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Cherbourg</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>2</th>
      <td>1</td>
      <td>3</td>
      <td>female</td>
      <td>26.0</td>
      <td>0</td>
      <td>0</td>
      <td>7.9250</td>
      <td>S</td>
      <td>Third</td>
      <td>woman</td>
      <td>False</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>True</td>
    </tr>
    <tr>
      <th>3</th>
      <td>1</td>
      <td>1</td>
      <td>female</td>
      <td>35.0</td>
      <td>1</td>
      <td>0</td>
      <td>53.1000</td>
      <td>S</td>
      <td>First</td>
      <td>woman</td>
      <td>False</td>
      <td>C</td>
      <td>Southampton</td>
      <td>yes</td>
      <td>False</td>
    </tr>
    <tr>
      <th>4</th>
      <td>0</td>
      <td>3</td>
      <td>male</td>
      <td>35.0</td>
      <td>0</td>
      <td>0</td>
      <td>8.0500</td>
      <td>S</td>
      <td>Third</td>
      <td>man</td>
      <td>True</td>
      <td>NaN</td>
      <td>Southampton</td>
      <td>no</td>
      <td>True</td>
    </tr>
  </tbody>
</table>
</div>




```python
db2.age.agg(['max','mean'])
```




    max     80.000000
    mean    29.699118
    Name: age, dtype: float64




```python
# Укажите процент выживших в аварии
```


```python
str(int((db2.survived[db2.survived==1].agg('count')/db2.survived.agg('count'))*100))+'%'
```




    '38%'




```python
#Создайте таблицу, в которой будет указано: минимальный возраст каждого пола, максимальный возраст каждого пола
```


```python
db2.groupby('sex', as_index=False).agg({'age':['min','max']})
```




<div>
<style scoped>
    .dataframe tbody tr th:only-of-type {
        vertical-align: middle;
    }

    .dataframe tbody tr th {
        vertical-align: top;
    }

    .dataframe thead tr th {
        text-align: left;
    }
</style>
<table border="1" class="dataframe">
  <thead>
    <tr>
      <th></th>
      <th>sex</th>
      <th colspan="2" halign="left">age</th>
    </tr>
    <tr>
      <th></th>
      <th></th>
      <th>min</th>
      <th>max</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>female</td>
      <td>0.75</td>
      <td>63.0</td>
    </tr>
    <tr>
      <th>1</th>
      <td>male</td>
      <td>0.42</td>
      <td>80.0</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Найдите, в каком классе мест пассажиров разница возрастов между самым старшим и самым младшим максимальна.
```


```python
db2.groupby('class', as_index=False).age.max().age-db2.groupby('class', as_index=False).age.min().age
```




    0    79.08
    1    69.33
    2    73.58
    Name: age, dtype: float64




```python
delta=db2.groupby('class', as_index=False).age.max() #Делаем ДФ с максимальными возрастами для каждого 
delta=delta.rename({'age':'age_old'}, axis=1) #Переименуем для удобства
delta['age_young']=db2.groupby('class', as_index=False).age.min().age #Добавляем колонку с минимальными возрастами
delta['age_d']=delta['age_old']-delta['age_young'] # добавляем третью с вычетом
print(delta)
print(f"Answer is {delta[delta.age_d==delta.age_d.max()]['class'][0]} class") #Выводим то значение, у которого разность возрастов будет совпадать с максимальным значением из списка
```

        class  age_old  age_young  age_d
    0   First     80.0       0.92  79.08
    1  Second     70.0       0.67  69.33
    2   Third     74.0       0.42  73.58
    Answer is First class
    


```python
# Есть два датафрейма. Объедините их с помощью Left join метода (то есть чтобы все значения из левой таблицы остались, даже если у правой таблицы нет значений для каких-то наименований)
```


```python
df1 = pd.DataFrame({'lkey': ['rabbit', 'wolf', 'parrot', 'rabbit','rabbit', 'wolf', 'parrot', 'rabbit','elephant'],
                    'kg': [1.2, 12.6, 0.4, 1.8,1.9, 11.1, 0.2, 1.6,340.4]})
df2 = pd.DataFrame({'rkey': ['rabbit', 'wolf', 'parrot','dolphin'],
                    'diet': ['carrot', 'meat', 'seeds','fish']})
```


```python
df1
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
      <th>lkey</th>
      <th>kg</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rabbit</td>
      <td>1.2</td>
    </tr>
    <tr>
      <th>1</th>
      <td>wolf</td>
      <td>12.6</td>
    </tr>
    <tr>
      <th>2</th>
      <td>parrot</td>
      <td>0.4</td>
    </tr>
    <tr>
      <th>3</th>
      <td>rabbit</td>
      <td>1.8</td>
    </tr>
    <tr>
      <th>4</th>
      <td>rabbit</td>
      <td>1.9</td>
    </tr>
    <tr>
      <th>5</th>
      <td>wolf</td>
      <td>11.1</td>
    </tr>
    <tr>
      <th>6</th>
      <td>parrot</td>
      <td>0.2</td>
    </tr>
    <tr>
      <th>7</th>
      <td>rabbit</td>
      <td>1.6</td>
    </tr>
    <tr>
      <th>8</th>
      <td>elephant</td>
      <td>340.4</td>
    </tr>
  </tbody>
</table>
</div>




```python
df2
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
      <th>rkey</th>
      <th>diet</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rabbit</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>1</th>
      <td>wolf</td>
      <td>meat</td>
    </tr>
    <tr>
      <th>2</th>
      <td>parrot</td>
      <td>seeds</td>
    </tr>
    <tr>
      <th>3</th>
      <td>dolphin</td>
      <td>fish</td>
    </tr>
  </tbody>
</table>
</div>




```python
#Если просто написать merge, то у нас пропадут некоторые данные, так как у нас было животное baz в первой таблице
df1.merge(df2, left_on='lkey', right_on='rkey')
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
      <th>lkey</th>
      <th>kg</th>
      <th>rkey</th>
      <th>diet</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rabbit</td>
      <td>1.2</td>
      <td>rabbit</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>1</th>
      <td>rabbit</td>
      <td>1.8</td>
      <td>rabbit</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>2</th>
      <td>rabbit</td>
      <td>1.9</td>
      <td>rabbit</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>3</th>
      <td>rabbit</td>
      <td>1.6</td>
      <td>rabbit</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>4</th>
      <td>wolf</td>
      <td>12.6</td>
      <td>wolf</td>
      <td>meat</td>
    </tr>
    <tr>
      <th>5</th>
      <td>wolf</td>
      <td>11.1</td>
      <td>wolf</td>
      <td>meat</td>
    </tr>
    <tr>
      <th>6</th>
      <td>parrot</td>
      <td>0.4</td>
      <td>parrot</td>
      <td>seeds</td>
    </tr>
    <tr>
      <th>7</th>
      <td>parrot</td>
      <td>0.2</td>
      <td>parrot</td>
      <td>seeds</td>
    </tr>
  </tbody>
</table>
</div>




```python
result=df1.merge(df2, left_on='lkey', right_on='rkey', how='left').drop('rkey', axis=1).rename({'lkey':'animal'},axis=1)
result
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
      <th>animal</th>
      <th>kg</th>
      <th>diet</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>0</th>
      <td>rabbit</td>
      <td>1.2</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>1</th>
      <td>wolf</td>
      <td>12.6</td>
      <td>meat</td>
    </tr>
    <tr>
      <th>2</th>
      <td>parrot</td>
      <td>0.4</td>
      <td>seeds</td>
    </tr>
    <tr>
      <th>3</th>
      <td>rabbit</td>
      <td>1.8</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>4</th>
      <td>rabbit</td>
      <td>1.9</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>5</th>
      <td>wolf</td>
      <td>11.1</td>
      <td>meat</td>
    </tr>
    <tr>
      <th>6</th>
      <td>parrot</td>
      <td>0.2</td>
      <td>seeds</td>
    </tr>
    <tr>
      <th>7</th>
      <td>rabbit</td>
      <td>1.6</td>
      <td>carrot</td>
    </tr>
    <tr>
      <th>8</th>
      <td>elephant</td>
      <td>340.4</td>
      <td>NaN</td>
    </tr>
  </tbody>
</table>
</div>


