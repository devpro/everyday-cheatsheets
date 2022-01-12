# Python

> Python is a programming language that lets you work quickly and integrate systems more effectively.

→ [python.org](https://www.python.org/)

## Learn

### Documentation

* [docs.python.org](https://docs.python.org/)

### Getting started

* [Beginner's Guide](https://wiki.python.org/moin/BeginnersGuide)
* [The Python Tutorial](https://docs.python.org/tutorial/index.html)

### Training

* [Python-Mini-Projects](https://github.com/Python-World/python-mini-projects)

## Step

### Installation

* [Downloads](https://www.python.org/downloads/)
* [How To Install Python 3 and Set Up a Programming Environment on an Ubuntu 20.04 Server](https://www.digitalocean.com/community/tutorials/how-to-install-python-3-and-set-up-a-programming-environment-on-an-ubuntu-20-04-server) (DigitalOcean) - October 29, 2021

## Practice

### Different ways to execute a command line

```python
from subprocess import call
print('Hello world!')
print(call(['dir'], shell=True))
call(['dotnet', 'My.Dll', 'Myparals'])

from subprocess import Popen, PIPE
cmd = 'blah'
p = Popen('dir', shell=True, stdout=PIPE, stderr=PIPE)
stdout, stderr = p.communicate()
print(stdout)
print(stderr)

import subprocess
print(subprocess.check_output(['dir'], shell=True))
print(subprocess.check_output(['dir'], shell=True).decode('iso-8859-15'))
print(subprocess.check_output(['dir'], shell=True).decode('iso-8859-15').encode('utf-8'))
print(subprocess.check_output(['dir'], shell=True).decode('windows-1255'))

import os
os.chdir('my_previous_path')
print(subprocess.check_output(['dotnet', 'My.Dll', 'Myparals']).decode('ascii'), end='\r\n')
```

Example:

```python
import os
from subprocess import Popen, PIPE

print "Hello World"

os.chdir('C:\\Users\\xxx\\Projets\\console-dotnet\\src\\ConsoleApp\\bin\\Debug\\netcoreapp2.0')

p = Popen('\"C:\\Program Files\\dotnet\\dotnet.exe" mapp.dll basic-info', shell=True, stdout=PIPE, stderr=PIPE)
stdout, stderr = p.communicate()
print(stdout)
print(stderr)
```
