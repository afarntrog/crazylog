# crazylog

**crazylog** logs like crazy. Allows to add extensive logging at each step in the python execution cycle.

# Installation

You can install from pypi:

``` bash
pip install -U crazylog
```

Or get the latest updates (Not recommended for production):

```bash
pip install -U git+https://github.com/afarntrog/crazylog.git
```

# Quickstart

Here you can see a few samples to get a feel of whats ahead.

## Basic example
```python
from crazylog import CrazyLogger

def foo():
   print('running code ...')

with CrazyLogger() as crazy:
   foo()

```

## Run it for specific classes only
```python
class CustomClass:
   pass

with CrazyLogger() as crazy:
   crazy.exclusively = [CustomClass]
   foo()
```


## Apply it manually to specific classes via metaclasses
#### Run the code as usual. `CrazyLogger` will kick in if that class is called
```python
from crazylog import CrazyLoggerMeta

class CustomClass(metaclass=CrazyLoggerMeta):
   def printer(self):
      print('CrazyLogger is active')

def foo():
   print('CrazyLogger will do nothing')
   CustomClass().printer()

# run as usual
foo()
```


## Apply it at the module level
#### `apply` should be added at the bottom of the module that you want it to take affect.
```python
# my_first_module.py
from crazylog import CrazyLogger

class CustomClass():
   def printer(self):
      print('CrazyLogger is active')

def foo():
   print('CrazyLogger is active')
   CustomClass().printer()

CrazyLogger.apply(__name__)

# my_second_module.py
from my_first_module import foo

def bar():
   print('CrazyLogger is not active in this module - only in my_first_module')

foo()

# CrazyLogger only has an effect when `foo` is called.

```


# Feedback and contributing

If you find something that can be improved please open an issue or even better, a PR, thank you.