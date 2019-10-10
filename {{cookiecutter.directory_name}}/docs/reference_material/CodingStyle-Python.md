# Best Practices Guide for Python

#### The Zen of Python
```Beautiful is better than ugly.
Explicit is better than implicit.
Simple is better than complex.
Complex is better than complicated.
Flat is better than nested.
Sparse is better than dense.
Readability counts.
Special cases aren't special enough to break the rules.
Although practicality beats purity.
Errors should never pass silently.
Unless explicitly silenced.
In the face of ambiguity, refuse the temptation to guess.
There should be one-- and preferably only one --obvious way to do it.
Although that way may not be obvious at first unless you're Dutch.
Now is better than never.
Although never is often better than *right* now.
If the implementation is hard to explain, it's a bad idea.
If the implementation is easy to explain, it may be a good idea.
Namespaces are one honking great idea -- let's do more of those!
```

### Style
Follow [PEP 8](https://www.python.org/dev/peps/pep-0008/), when sensible.

##### Naming
- Variables. functions, methods, packages, modules
 - `lowercase_with_underscores`
- Classes and exceptions
  - `CamelCase`
- Protected methods and internal methods
 - `_single_leading_underscore(self, ...)`
- Private methods
 - `__double_leading_underscore(self, ...)`
- Constants
 - `ALL_CAPS_WITH_UNDERSCORE`
<br>
<br>

#### General Naming Guidelines
Avoid one-letter variables (especially `l`, `O`, `I`) <br>
_exception:_ In very short blocks, when the meaning is clearly visible from immediate context
###### Fine
```python
for e in elements:
  e.mutate()
```

<br>

Prefer "reverse notation"
###### Yes
```python
elements = ...
elements_active = ...
elements_defunct = ...
```
###### No
```python
elements = ...
active_elements = ...
defunct_elements ...
```
<br>

Avoid getter and setter methods
###### Yes
```Python
person.age = 42
```
###### No
```python
person.set_age(42)
```

<br>

##### Indentation
Use 4 spaces -- never tabs.

<br>

##### Imports
Import entire modules instead of individual functions within a module. for example,
a top-level module `webstat` that has a file `webstat/sessions.py`
###### Yes
```Python
import webstst
import webstat.sessions
from webstat import sessions
```
###### No
```Python
from webstat import get_user_stat # function from webstat/__init__.py
from webstat.sessions import get_session # function from webstat/sessions.py
```
_Exception:_ from third-party code where documentation explicitly says to import individual functions
_Rationale:_ Avoids circular imports.

<br>
Put all imports at the top of the page with three sections, each separated by a blank line, in this order:

1. System imports
1. Third-party imports
1. Local source tree imports

_Rationale:_ Makes it clear where each module is coming from

<br>

###### Documentation
Follow [PEP 257](https://www.python.org/dev/peps/pep-0257/)'s docstring guidelines.
Use one-line docstrings for obvious functions.
```Python
"""Return the length of each session."""
```

Multi-line docstrings should include
- Summary line
- Use case, if appropriate
- Args
- Return type and semantics, unless `None` is returned

```Python
"""Train a model to classify Foos and Bars.

Usage::

    >>> import klassify
    >>> data = [("green", "foo"), ("orange", "bar")]
    >>> classifier = klassify.train(data)

:Args:
    train_data: A list of tuples of the form ``(color, label)``.
:Return:
    A :class:`Classifier <Classifier>`
"""
```
Notes
- Use action words ("Return") rather than descriptions ("Returns")
- Document `__init__` methods in the docstring for the class
```Python
class Person(object):
    """A simple representation of a human being.

    :param name: A string, the person's name.
    :param age: An int, the person's age.
    """
    def __init__(self, name, age):
        self.name = name
        self.age = age
```

<br>

###### Comments
Use sparingly. Prefer code readability to writing a lot of comments. Often, small methods are more effective than comments.

###### No
```Python
# If the sign is a stop sign
if sign.color == 'red' and sign.sides == 8:
    stop()
```

###### Yes
```Python
def is_stop_sign(sign):
    return sign.color == 'red' and sign.sides == 8

if is_stop_sign(sign):
    stop()
```

use cases:
- explaining legacy code that cannot be altered.
- explaining logic used (why an obvious better way was not taken)

###### Block comments

Block comments can be used to explain more complicated code or code that you don’t expect the reader to be familiar with. These longer-form comments apply to some or all of the code that follows, and are also indented at the same level as the code.

In block comments, each line begins with the hash mark and a single space. If you need to use more than one paragraph, they should be separated by a line that contains a single hash mark

<br>

###### Line lengths
80 - 100 characters are acceptable.

Use paranthesis for line continuations. Avoid backslash for line continuation.
```Python
my_very_big_string = (
    "For a long time I used to go to bed early. Sometimes, "
    "when I had put out my candle, my eyes would close so quickly "
    "that I had not even time to say “I’m going to sleep.”"
)
```
_Exceptions:_
- Long import statements
- URLS, pathnames, or long flags in Comments
- Long string module level constants not containing whitespace that would be inconvenient to split across lines such as URLs or pathnames.

###### Yes
```python
# See details at
# http://www.example.com/us/developer/documentation/api/content/v2.0/csv_file_name_extension_full_specification.html
```
###### No
```Python
# See details at
# http://www.example.com/us/developer/documentation/api/content/\
# v2.0/csv_file_name_extension_full_specification.html
```
