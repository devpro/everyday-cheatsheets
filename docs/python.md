# Python

## Recipes

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
