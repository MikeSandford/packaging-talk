
# Python Packaging & Publishing

How to organize your code into a python package that can be installed with pip and published to pypi or other python repositories.

!SLIDE

## Why package up your python?

!SLIDE

### Would you rather?
```
git clone git@github.com:me/my-project.git
cd my-project
pip install -r requirements.txt
echo "$PATH=~/my-project/:$PATH" >> ~/.bashrc
python do_something.py
```
vs
```
pip install my-project
do_something
```

!SLIDE

### Dependency management

`` git submodules `` vs `` pip install my-project==0.2.7 ``


!SLIDE

### CLI Tools

Entry points are a way to make your python program available neatly
```
entry_points={
          'console_scripts': [
              'my_project = my_project.__main__:main'
          ]
      },
```

!SLIDE

### Distribution!
What you need to easily distribute your software via:

1.  public pypi
2.  private pypi repo (internal to company, say)
3.  just from github

!SLIDE

## Why distribute your code?

!SLIDE
### To give back to the awesome python community

![batteres included](../images/python.png "Batteries Included")

!SLIDE

### Career building
It's far easier to get hired with good work in the public eye

![hire me](../images/kenneth_reitz.png "Kenneth Reitz")
vs
![less great](../images/mike_sandford.png "Mike Sandford")

!SLIDE

### You actually want other people to use it

```
pip install package-name
```
vs
```
git clone github.com:someguy/someproject.git
cd someproject
vi README
pip install -r requirements.txt
// scratches head???
// gives up *shrug*
```


!SLIDE

## How to create a package



!SLIDE

## How to publish to pypi
