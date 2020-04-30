# New-pandas-users-summary
This is a summary of basic functions and concepts from pandas tutorial for new users, focusing on creating dataFrame, grouping, IO, lambda, selecting data and handling indexs etc the very necessity of using pandas. 

I first list the functions together to give a overview :
## List of functions:
[references--from pandas documentation](https://pandas.pydata.org/pandas-docs/version/0.15/tutorials.html)
### **Remeber coding is a LANGUAGE, to be able to speak that language, you need to remember the words first. The functions below are the words, finding oppotunities to use them over and over again. Even if you may not know exactly, you will develop a sense along the way.** 

- list
- zip
> **list(zip(names, numbers))**
- pd.DataFrame(data = , columns=[])
- df.to_csv
- pd.read_csv
- df.types (check datatype of column)
- df.sort_values([column_name], ascending = True or False )
- df.sort_index(axis=0)

- random.seed()
- random.randint(low = , high = )

> **random_names = [names[random.randint(low=0 high = len(names))] for i in range(1000)]**

- len
- range
- df.info()
- df.describe()
- df[column_name].unique()

- df.groupby('index')
- df.groupby().sum()

- def function():
   return

- pd.read_excel(path, index_col = )
- df.index

> **df['State'] = df.State.apply(lambda x: x.upper())**
> **df = df[df['Status'] == 1] boolean indexing**

- df.reset_index()
> **Daily = df.reset_index().groupby(['State','StatusDate']).sum()**

- del df[column_name]
- df.index.levels[0]

> **StateYearMonth = Daily.groupby([Daily.index.get_level_values(0), Daily.index.get_level_values(1).year, Daily.index.get_level_values(1).month])**
> **Daily['Lower'] = StateYearMonth['CustomerCount'].transform(lambda x: x.quantile(q=.25) - (1.5x.quantile(q=.75) - x.quantile(q=.25)))**
> **YearMonth = All.groupby([lambda x: x.year, lambda x:x.month])**

- idx = pd.date_range(start = , end = , freq= )
- df = pd.DataFrame(data, index = idx, columns = [columns_name])
- pd.concat()
> **Year = combined.gropupby(lambda x:x.year).max()**
- df.pct_change(periods = )

- df.iloc[0:3]
- df[column_name]
- df.loc[df.index[0:3], column_name]

> **d = {'one':[1,1], 'two':[2,2]}**
> **i = ['a', 'b']**
> **df = pd.DataFrame(data = d, index = i)**


```
     one	two
  a	1	2
  b	1	2
```

- df.stack()

```

 a  one    1
    two    2
 b  one    1
    two    2
```

- df.unstack()

```

 one  a    1
      b    1
 two  a    2
      b    2
```

- df.T

```
        a  b
 one	  1	1
 two	  2	2
```

- df.copy()

> calculate outlier
> **newdf['Outlier'] = State.transform(lambda x: abs(x-x.mean()) > 1.96x.std())**
- df.to_json()
- df.pd.read_json()
> combining data from different resource

> 1.getting file name list


```
FileNames = []
os.chdir(r"path")
for files in os.listdir('.'):
    if files.endswith(".xlsx"):
        FileName.append(files)
```

>2. getting files

```

def GetFile(fnambre):
    location = r'path\' + fnambre
    df = pd.read_excel(location, 0)
    df['File'] = fnambre
    return df.set_index([File])
```

>3.Creating a list of dataframes

```

df_list = [GetFile(fname) for fname in FileNames]
big_df = pd.concat(df_list)
```
#### I find after learn from the examples, making yourown user case is very helpful to check understanding and see if you are really able to use them solve problems. Learning by doing is a very effective way. Let us start with an example I made:
use function random.randin and for loop based on certain lists you basically can create a dtaset as large, time is a normal index especailly in time serises data so creating date with pd.date_range is also useful. Assigning data, index and columns respectively, a dataset is made. Then, other functions can be used to practice abstracting subdataset, manipulating date to answer questions.

I first created a dataset with dates as index, name, age, nationality etc as columns. I asked myself to answer "an odd" question: "Does the popularity of different names chage with time? " This is a classic question to practice abstract subdataset. I first used df.sort_index() to make the date index in desending order. after that I used df.reset_index().groupby().sum() to first divide dataset by Names, second by year, then sum up the number of each group, question answered. Basically three lines of code.

You can try to answer "Are there more female migrants than male migrants from different country?"

Remember that you will encounter problems that seems very simple and easy but you just do not know where went wrong! Be patient with yourself, nothing wring with you, the language of machine is dull and picky, you have to first follow its rules, second do not be afraid of trying, make every possible changes to see what happen, start from simple version. Even many times your problem isnt solved but you learn something.  


# Pandas cookbook summary
This is a supplyment of the first section. From pandas cookbook. 
[References--Pandas documentaion pandas cookbook](https://nbviewer.jupyter.org/github/jvns/pandas-cookbook/blob/v0.1/cookbook/Chapter%201%20-%20Reading%20from%20a%20CSV.ipynb)
## List of functions:
- pd.read_csv('path', sep = ':', encoding='Latins1', parse_dates=['Date'], dayfirst=True, index_col = 'Date')
- df[column_name].plot(kind = )
### Dealing with columns that is text represnts different item ###
- df[column_name].value_counts()
### a more serious slicing and dicing ###
- df[colum_name1 == 'condition' & column_name2 == 'condition']

- astype(float)
- df.index.weekday
- 



