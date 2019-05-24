pip get wheel files
* pip wheel pkg_name # it will download whl in the current directory (include dependency)

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