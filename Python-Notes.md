
### backtrace
 * import logging
 * logging.error('error is: ' % str(err), exc_info=True, stack_info=True)
 
###  Print Function (for python2 code (?))
```
from __future__ import print_function
```
pip get wheel files
* pip wheel pkg_name # it will download whl in the current directory (include dependency)
Checking around, it seems using commands like

pip download -d WHL_DIR pkg_name # some pkg exists in tar.gz, why?

or

pip wheel pkg_name # all pkgs in whl format.

can generate something with human-readable file names that's manageable.
And use

pip install -f file///DIR pkg_name

to install. Some say use pip-accel makes it easier, but I didn't try that. Not sure how we can combine both designs into one.


List not used import
* pyflakes file.py

setuptools
* python3 setup.py install --user

Packages:
 * https://github.com/bndr/pipreqs: Generate pip requirements.txt file based on imports of any project

Misc:
 * anaconda: https://www.anaconda.com/download/, for Data Science, lots of library included, large download size.
 *

Cleanly remove python in OSX:
 * To remove python installation: (ex: version 3.5)
 * remove files like  /Library/Frameworks/Python.framework/Versions/3.5
 * remove /Applications/Python\ 3.5
 * remove link from /usr/local/bin that point to files in /Library/Frameworks/Python.framework/Versions/3.5/bin/
 * remove path in ~/.bash_profile