
# Python Packaging & Publishing

How to organize your code into a python package that can be installed with pip and published to pypi or other python repositories.

### Mike Sandford
#### Arundo Analytics
http://www.arundo.com

!SLIDE

## Why package up your python?

!SLIDE

### Would you rather?
```
pip install my-project
do_something
```
or
```
git clone git@github.com:me/my-project.git
cd my-project
pip install -r requirements.txt
echo "$PATH=~/my-project/:$PATH" >> ~/.bashrc
python do_something.py
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
### To give back to the awesome python community!

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

1.  Have some working code
2.  Create a setup.py file
3.  Profit!

!SLIDE

### v0

* Just barely works
* Where most of us start

!SLIDE

### v1

 * Better, using argparse rather than sys.argv
 * Can we do better?

!SLIDE
### v1.1

* Uses setup.py so installable
* No "package hygiene" -> look in virtualenv

!SLIDE
### v1.2

* Installable
* Hygienic
* Not easy to use from shell

!SLIDE
### v1.3

* Installable
* Package-hygienic
* CLI binary

!SLIDE
### v2.0

* Installable
* Package-hygienic
* CLI binary
* Includes dependencies
* Easy to read/understand

!SLIDE
### v2.1

* Installable
* Package-hygienic
* CLI binary
* Includes dependencies
* Easy to read/understand
* Documented!

!SLIDE
## How to publish to pypi

I started with these directions:
http://peterdowns.com/posts/first-time-with-pypi.html

Turns out they're totally wrong now!

1.  Register accounts with test and prod
2.  Create a .pypirc file
3.  Publish in test
4.  Publish in prod

!SLIDE

### Register accounts

![not too hard](../images/not_too_hard.png "Just go for it")

!SLIDE
### Create .pypirc file

```
[distutils]
index-servers =
  pypi
  testpypi

[pypi]
repositoy=https://pypi.python.org/pypi
username=MikeSandfordArundo
password=WHOAWHOAWHOA

[testpypi]
repository=https://test.pypi.org/legacy/
username=MikeSandfordArundo
password=WHOAWHOAWHOA
```


!SLIDE
### Publish in test
#### v2.2

```
(virt) sandford@mjolnir ~/talks/echoer $ python setup.py sdist
/usr/lib/python3.5/distutils/dist.py:261: UserWarning: Unknown distribution option: 'entry_points'
  warnings.warn(msg)
/usr/lib/python3.5/distutils/dist.py:261: UserWarning: Unknown distribution option: 'install_requires'
  warnings.warn(msg)
running sdist
running check
warning: sdist: manifest template 'MANIFEST.in' does not exist (using default file list)

warning: sdist: standard file not found: should have one of README, README.txt

writing manifest file 'MANIFEST'
creating Echoer-2.2
creating Echoer-2.2/echoer
making hard links in Echoer-2.2...
hard linking setup.cfg -> Echoer-2.2
hard linking setup.py -> Echoer-2.2
hard linking echoer/__init__.py -> Echoer-2.2/echoer
hard linking echoer/cli.py -> Echoer-2.2/echoer
creating dist
Creating tar archive
removing 'Echoer-2.2' (and everything under it)
(virt) sandford@mjolnir ~/talks/echoer $ twine upload --repository-url https://test.pypi.org/legacy/ dist/*
Uploading distributions to https://test.pypi.org/legacy/
Enter your username: MikeSandfordArundo
Enter your password:
Uploading Echoer-2.2.tar.gz
100%|███████████████████████████████████████████████████████████████| 3.42k/3.42k [00:01<00:00, 3.31kB/s]
(virt) sandford@mjolnir ~/talks/echoer $
```

!SLIDE
### Publish in prod

```
(virt) sandford@mjolnir ~/talks/echoer $ twine upload dist/*Uploading distributions to https://upload.pypi.org/legacy/
Uploading Echoer-2.2.tar.gz
100%|███████████████████████████████████████████████████████████████| 3.42k/3.42k [00:00<00:00, 14.6kB/s]
(virt) sandford@mjolnir ~/talks/echoer $
```

!SLIDE

# Questions?




!SLIDE

# Shameless Promotion

## Arundo Analytics
### We're Hiring!

http://www.arundo.com/
