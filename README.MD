# `vollib`

This was forked from [vollib](https://github.com/vollib/vollib) so that this module along with [lets_be_rational](https://github.com/vollib/lets_be_rational) can be used in Python 3.5. 

### Description of vollib from original vollib package:

`vollib` is a python library for calculating option prices, 
implied volatility and greeks. At its core is Peter Jäckel's 
source code for `LetsBeRational`, an extremely fast and accurate algorithm 
for obtaining Black's implied volatility from option prices.

Building on this solid foundation, `vollib` provides functions 
to calculate option prices, implied volatility and greeks using 
Black, Black-Scholes, and Black-Scholes-Merton. `vollib` 
implements both analytical and numerical greeks for each of the three pricing formulae.

### Dependencies

Refer to the most the original [vollib](https://github.com/vollib/vollib) documentation for questions on dependencies. One important dependency is [SWIG](http://www.swig.org/download.html). Note that for Ubuntu users, SWIG is in the Ubuntu repository and can be installed with

```
sudo apt-get install swig
```

### How to install

Note that this has not been well tested, and these directions are for installing on a Linux computer. Adapting these directions for another operating system should be easy enough though. 

First, download the source code from this module with this [link](https://github.com/carterkd/vollib/archive/master.zip) and from the `lets_be_rational` module with this [link](https://github.com/carterkd/lets_be_rational/archive/master.zip). Unzip these. Then (this is Linux specific) open the unzipped `lets_be_rational` folder, and change the line in `make_linux.sh` that has
```
gcc -c src/erf_cody.cpp src/rationalcubic.cpp src/normaldistribution.cpp src/LetsBeRational.cpp src/LetsBeRational_wrap.c -I/usr/include/python2.7
```
to
```
gcc -c -fPIC src/erf_cody.cpp src/rationalcubic.cpp src/normaldistribution.cpp src/LetsBeRational.cpp src/LetsBeRational_wrap.c -I/path/to/header/file/
```
Where you should replace `/path/to/header/file/` with the actual path to the Python 3.5 header file named `Python.h` on your computer. Note that if you are using [Anaconda](https://www.continuum.io/downloads) with Python 3.5.2-0, this path will look something like `/home/myusername/anaconda3/pkgs/python-3.5.2-0/include/python3.5m/`. This directory can be found by searching in a directory through various subdirectories with the command `find /search/directory -iname Python.h` (for example `find / -iname Python.h` will search your entire computer). Once this change is made, create the shared library by running:
```
./make_linux.sh
```

After this, to install this module run
``` 
python setup.py install
``` 

Now open the `vollib` source code folder you downloaded, and install it with the command:
```
python setup.py install
```

That's it! You should now be able to use `vollib` in Python 3.5!

### What did I change from the original vollib module source code?

All I did was downloaded the [vollib](https://github.com/vollib/vollib) and [lets_be_rational](https://github.com/vollib/lets_be_rational) source code (on 11/23/2016) and in the respective directories, used [2to3](https://docs.python.org/3.0/library/2to3.html) to change the code from Python 2.x to Python 3.x code with the commands
```
2to3 -wn vollib-master
```
```
2to3 -wn lets_be_rational-master
```

That's it! If you want a more up-to-date version of [vollib](https://github.com/vollib/vollib) and [lets_be_rational](https://github.com/vollib/lets_be_rational), head over there, and do this yourself!
