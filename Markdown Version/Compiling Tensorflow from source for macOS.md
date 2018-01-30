# Compiling Tensorflow from source for MacOS

1. Install Xcode and Xcode command line tools.
2. Disable SIP following [these](https://studionetworksolutions.zendesk.com/hc/en-us/articles/115003839246-How-to-disable-Systems-Integrity-Protection-SIP-in-macOS) instructions. Enable it back once everything is compiled and running.
3. Install [homebrew](https://brew.sh).
4. Install [bazel](https://docs.bazel.build/versions/master/install.html#mac-os-x) (Needs JDK).
5. Install [conda](https://conda.io/miniconda.html).
6. Then in Terminal: `$ sudo pip install six numpy wheel `
7. `$ git clone https://github.com/tensorflow/tensorflow`
8. `$ cd tensorflow`
9. `$git checkout r1.4` (change it to current verion)
10. `$ bazel clean`
11. `$ ./configure`

12. You'll get something like this, just install what you need:

```

Please specify the location of python. [Default is /usr/bin/python]: /usr/bin/python2.7
Found possible Python library paths:
  /usr/local/lib/python2.7/dist-packages
  /usr/lib/python2.7/dist-packages
Please input the desired Python library path to use.  Default is [/usr/lib/python2.7/dist-packages]

Using python library path: /usr/local/lib/python2.7/dist-packages
Do you wish to build TensorFlow with MKL support? [y/N]
No MKL support will be enabled for TensorFlow
Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]:
Do you wish to use jemalloc as the malloc implementation? [Y/n]
jemalloc enabled
Do you wish to build TensorFlow with Google Cloud Platform support? [y/N]
No Google Cloud Platform support will be enabled for TensorFlow
Do you wish to build TensorFlow with Hadoop File System support? [y/N]
No Hadoop File System support will be enabled for TensorFlow
Do you wish to build TensorFlow with the XLA just-in-time compiler (experimental)? [y/N]
No XLA support will be enabled for TensorFlow
Do you wish to build TensorFlow with VERBS support? [y/N]
No VERBS support will be enabled for TensorFlow
Do you wish to build TensorFlow with OpenCL support? [y/N]
No OpenCL support will be enabled for TensorFlow
Do you wish to build TensorFlow with CUDA support? [y/N] Y
CUDA support will be enabled for TensorFlow
Do you want to use clang as CUDA compiler? [y/N]
nvcc will be used as CUDA compiler
Please specify the Cuda SDK version you want to use, e.g. 7.0. [Leave empty to default to CUDA 8.0]: 8.0
Please specify the location where CUDA 8.0 toolkit is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:
Please specify which gcc should be used by nvcc as the host compiler. [Default is /usr/bin/gcc]:
Please specify the cuDNN version you want to use. [Leave empty to default to cuDNN 6.0]: 6
Please specify the location where cuDNN 6 library is installed. Refer to README.md for more details. [Default is /usr/local/cuda]:
Please specify a list of comma-separated Cuda compute capabilities you want to build with.
You can find the compute capability of your device at: https://developer.nvidia.com/cuda-gpus.
Please note that each additional compute capability significantly increases your build time and binary size.
[Default is: "3.5,5.2"]: 3.0
Do you wish to build TensorFlow with MPI support? [y/N] 
MPI support will not be enabled for TensorFlow
Configuration finished
```

13. Leave this answer in its default: `Please specify optimization flags to use during compilation when bazel option "--config=opt" is specified [Default is -march=native]`
14. Then : `$ bazel build -c opt --copt=-mavx --copt=-mavx2 --copt=-mfma --copt=-msse4.1 --copt=-msse4.2 --config=opt -k //tensorflow/tools/pip_package:build_pip_package`
15. Any errors encountered try to solve using [this thread](https://github.com/tensorflow/tensorflow/issues/6729).
16. Build the wheel file: `$ bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow_pkg`
17. Finally: `$ pip install --upgrade --ignore-installed /tmp/tensorflow_pkg/tensorflow-1.4.1-cp36-cp36m-macosx_10_7_x86_64.whl`

#### For GPU installation:
Follow [this guide](https://gist.github.com/philster/042fabcf73f2269e6b1e6d28fbeeb7e3).

#### Debug Stuff:
Compiled Wheel File is found in:
> Macintosh HD->tmp->tensorflow_pkg 
`/private/tmp/tensorflow_pkg`

Some permission problems can be solved using:

```
$ sudo chown -R USERNAME /Users/USERNAME/FOLDER
```

#### References:
[Official Guide](https://www.tensorflow.org/install/install_sources#PrepareMac)
[Stackoverflow](https://stackoverflow.com/questions/41293077/how-to-compile-tensorflow-with-sse4-2-and-avx-instructions)



