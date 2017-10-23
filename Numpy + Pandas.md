# Numpy + Pandas

## Concept

- ndarray is mutable

## Numpy

###Basic 

```py
# create ndarray
arr = np.random.random(0,10,10)
# Create vector from 10 to 20
arr1 = np.arange(10,20)

# insert element/array
np.insert

# delete element
np.delete

# modify value
# assign directly, since ndarray is mutalbe, assignment is inplace

# indexing value
arr[start:end:step]
arr[(arr>a) & (arr<b)]

# map/filter/reduce array
vectorize
apply_along_axis

# sort array（sort is inplace）
arr.sort()

# compare two lists, get elements that in l1 but not in l2
list(set(l1) - set(l2))
```

## Pandas

### DataType

```python
# convert datatype
df['col1'].astype(int)

# datetime
pd.to_datetime(df['col1'])
# compute date diff in specific unit
df['month'] = (df.date2 - df.date1)/ np.timedelta64(1, 'M')
```

### Basic DataFrame Manipulation

```python
# rename column
df.rename(index=str, columns={old_name:new_name})

# Compare Series
s1  = pd.Series(l1)
s1.isin(l2)

###############################################################
# columns
###############################################################
# sort by multiple columns
df.sort_values(['col1', 'col2'], ascending=[True, False])
# select columns with specific datatype
df.loc[:, df.dtypes == 'float64']

###############################################################
# rows
###############################################################
# add one row at the bottom of df
df.loc[df.shape[0]] = [val1, val2, ...]
# iterate over rows
for idx,row in df.iterrows():
	#code comes here

###############################################################
# NaN
###############################################################
# select row with all NaN
df.isnull().all(1)

```

###  Groupby 

1.  Basic Manipulation
```python
## implementation 1
df.groupby(['col1', 'col2'], as_index = False)['col3'].agg({'max':np.max, 'sum':np.sum})

## implementation 3
df.groupby(['col1', 'col2'])['col3'].agg({'max':np.max, 'sum':np.sum})

## implementation 3
df.groupby(['col1', 'col2'], as_index = False)['col3'].agg([np.max,np.sum])

## implementation 4
df.groupby(['col1', 'col2'], as_index = False)['col3', 'col4'].agg({'max':np.max, 'sum':np.sum})

## only implementation 1 will generate dataframe with one layer of column
## imp 2 doesn't use as_index in groupby, so col1 and col2 will be used as index.
## the way imp 3 use agg function will generate multiple layer of column in result dataframe.
## imp 4 use more than one target column(col3 and col4), therefore the output dataframe
## will contains multiple layer of column.
## So, use imp 1 to group dataframe to generate clean dataframe
```
**Groupby tends to be slow when there are too many distinct groups. Vectorized operation rather than for loop will help to decrease running time. And returning df in method in apply should be avoid. If the the method in apply returns df, a new copy of df will be created which slows down implementation** 

2. MultiIndex
  reset_index can convert multipleindex back to one layer index. Any you can also specify which level of multiindex to drop, by defining argument 'level'

3. over (partition by order by)
```python
# use predefined function to implement on sub_df
def func(df, arg1, arg2):
	#do something on df
	return df
gb = df.groupby(['col1', 'col2'], as_index=False)
result = gb.apply(func, arg1, arg2)
```

### Apply/Map/Applymap
1.  Discrete Value to Value Map
```python
# define a dictionary of mapping, then use map function.
# by using this function, if any value that is not a key of dict object,
# output value will be NaN
dict = {'A':1, 'B':2}
df['col1'].map(dict)
```
2.  Range of Value to Value Map
```python
# If input is a range of continous value, then use pandas cut function.
# the argument 'labels' should be set to False, because we want the function to return only integers,
# if set to True, function will return range such as '(a,b]'.

col1_mapped = pd.cut(df['col1'], [0,5,10,20], labels=False)
output_value_table = ['A', 'B', 'C'] 
col1_mapped = output_value_table[col1_mapped]
```
3.  Apply by a predefined function
```python
# 1. Series apply function
# 2. Numpy apply along axis

# 3. Use function and vectorized function
# apply can be slow

def func(num1, num2):
	return num1+num2
func_vec = np.vectorize(func)

result_list = func_vec(col1, col2)
```





