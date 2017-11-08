# python

## Questions

1. difference between single and double underscore, such as
```python
   __name__
   __main__
   __init__
   __doc__
   __all__
   __builtins__
```

2. multiprocessin/thread



## Concepts

### namespace
mapping from names to objects

- difference between 'and' <=> &, 'or' <=> |
  'and' and 'or' are logicall operator,
  & and | are bitwise operator

### Basic
```python
# ternary conditional operator
val1 if condition else b

########################
# delete
########################
# delete by value(only first occurance will be deleted)
li.remove(a)
# delete by index
del li[1]

# compare two lists, get elements that in l1 but not in l2
list(set(l1) - set(l2))

# concate two list
li = li1 + li2
```

### Variable Type

```python
# float keep two digit of decimal
# 1 use round method
round(flt,2)
# 2 use format method
format(flt, ".2g")
```

###  module

1. use module
  import module as alias
  import package.module as alias
  from package.subpackage import module as alias
  from package.module import function		

2. create module
  a py file is a module

3. package
  a folder with \__init__.py file is a package

4. import module from upper level directory

```py
import sys
sys.path.append('..')
```
* example

considering file struture as below:

sound - \__init__.py
      - module1.py

1. if in \__init__.py we say: import module1
  it will not work, becuase interpreter will try to find module1.py at sound level.
  Instead, we should use: from . import module1

2. import a module multiple times will not reload the module multiple times,
  reload function will reload the module again

3. when reload(package), it will run \__init__.py in package
  when reload(module), it will run module.py


### class
    1. when class variable is pointing to a dataframe, the dataframe is passed by reference.
```python
	class Test:
		def __init__(self, df):
			self.df = df
		 
	## define new dataframe
	df
	
	t1 = Test(df)
	t2 = Test(df)
	t3 = Test(df)
	
	# id(t1.df),id(t1.df),id(t1.df) are all the same
```

### enum

```python
from enum import Enum

class ImpurityCriteria(Enum):
    Entropy = 1
    Gini = 2
    Unknown = 3

ImpurityCriteria.Entropy.value # return 1
	
```

### Data Structure

* List

```python
# create
li = []

# delete
del li[index]

# delete multiple by index
removelist = [0,2,3] # a list contains index of elements to remove
newli = [v for i, v in enumerate(li) if i not in removelist]

# Functional Programming
filter(func, li)
map(func, li)
reduce(func, li)
```




