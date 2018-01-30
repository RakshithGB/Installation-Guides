# Useful Python Libraries
This guide shows steps to install some useful 3rd party libraries for Computer Vision and Machine Learning applications on macOS.

## Dlib
This handy library was created in C++ by Davis King and contains many useful functions like Face Detector, Object Detector, Sequence Segmentor etc. More details on this library can be found on the official [website](http://dlib.net/compile.html).

We can install this in python.
Initial requirements:


```
$ brew install cmake
$ brew install boost
$ brew install boost-python --with-python3
```

This will take some time, once thats done check if boost installed correctly by:


```
$ brew list | grep 'boost'
boost
boost-python
```

As you can see from my terminal output, both Boost and Boost. Python have been successfully installed.

Then install [XQuartz](https://www.xquartz.org). Just download the `.dmg` file and install. 

With `pip`:

```
$ pip install dlib
```

With `conda` (recommended):

```
$ conda install -c menpo dlib 
```

## Scikit-image, Scikit-learn, Scipy, Numpy
Handy mathematics libraries for python.
Websites: [SciPy](https://scipy.org), [Scikit-image](http://scikit-image.org), [Scikit-learn](http://scikit-learn.org/stable/)

With `pip`:

```
$ pip install numpy
$ pip install scipy
$ pip install scikit-image
$ pip install scikit-learn
```

With `conda`:


```
$ conda install scipy 
$ conda install scikit-image 
$ conda install numpy
$ conda install scikit-learn 
```

## Imutils
Handy image processing functions developed by Adrian Rosebrock. Official [blog](http://www.pyimagesearch.com/2015/02/02/just-open-sourced-personal-imutils-package-series-opencv-convenience-functions/).

```
$ pip install --upgrade imutils
```
## Tensorflow
A great machine learning library. Website [link](https://www.tensorflow.org).

```
pip install tensorflow 
```
## Keras
The simplest package to use for machine learning. Official [Website](https://keras.io).

Install `Tensorflow` first if you need that as the backend. (recommended)

It's ideal to have these packages before installing keras:

```
$ pip install numpy scipy
$ pip install scikit-learn
$ pip install pillow
$ pip install h5py
```
Then:

```
$ pip install keras
```
To verify its using `Tensorflow` as backend navigate to `~/.keras/keras.json` and open the file in text editor.

It would show:

```
{
    "floatx": "float32",
    "epsilon": 1e-07,
    "backend": "tensorflow",
    "image_data_format": "channels_last"
}
```
Make changes to this file to set the required backend.

## Tesseract OCR
A light weight text recognition engine open sourced by Google. GitHub [source](https://github.com/tesseract-ocr/tesseract).

Wrapper:

```
$ pip install pytesseract
```

## Play Sound
Light weight package to play sounds from files.

```
$ pip install playsound
$ pip install pyobjc
```

## Updating All Packages
For `pip` install:

```
$ pip install pipdated
```
Then everytime update all pip packages using:

```
$ sudo -H pipdate
```

For `brew`:

```
$ brew upgrade
```

For `conda`:

```
$ conda update --all
```

## Intel MKL 


```
$ conda install mkl -c intel --no-update-deps
$ conda install numpy -c intel --no-update-deps
```



