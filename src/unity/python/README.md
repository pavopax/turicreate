<img align="right" src="https://docs-assets.developer.apple.com/turicreate/turi-dog.svg" alt="Turi Create" width="100">

# Turi Create 

Turi Create simplifies the development of custom machine learning models. You
don't have to be a machine learning expert to add recommendations, object
detection, image classification, image similarity or activity classification to
your app.

* **Easy-to-use:** Focus on tasks instead of algorithms
* **Visual:** Built-in, streaming visualizations to explore your data
* **Flexible:** Supports text, images, audio, video and sensor data
* **Fast and Scalable:** Work with large datasets on a single machine
* **Ready To Deploy:** Export models to Core ML for use in iOS, macOS, watchOS, and tvOS apps

Example: Image classifier with a few lines of code
--------------------------------------------------

If you want your app to recognize specific objects in images, you can build your own model with just a few lines of code:

```python
import turicreate as tc

# Load data
data = tc.SFrame('photoLabel.sframe')

# Create a model
model = tc.image_classifier.create(data, target='photoLabel')

# Make predictions
predictions = model.predict(data)

# Export to Core ML
model.export_coreml('MyClassifier.mlmodel')
```
 
It's easy to use the resulting model in an [iOS application](https://developer.apple.com/documentation/vision/classifying_images_with_vision_and_core_ml):

<p align="center"><img src="https://docs-assets.developer.apple.com/published/a2c37bce1f/689f61a6-1087-4112-99d9-bbfb326e3138.png" alt="Turi Create" width="600"></p>

With Turi Create, you can can tackle a number of common scenarios:
* [Recommender systems](https://apple.github.io/turicreate/docs/userguide/recommender/introduction.html)
* [Image classification](https://apple.github.io/turicreate/docs/userguide/image_classifier/introduction.html)
* [Image similarity](https://apple.github.io/turicreate/docs/userguide/image_similarity/introduction.html)
* [Object detection](https://apple.github.io/turicreate/docs/userguide/object_detection/introduction.html)
* [Activity classifier](https://apple.github.io/turicreate/docs/userguide/activity_classifier/introduction.html)
* [Text classifier](https://apple.github.io/turicreate/docs/userguide/text_classifier/introduction.html)

You can also work with essential machine learning models, organized into algorithm-based toolkits:
* [Classifiers](https://apple.github.io/turicreate/docs/userguide/supervised-learning/classifier.html)
* [Regression](https://apple.github.io/turicreate/docs/userguide/supervised-learning/regression.html)
* [Graph analytics](https://apple.github.io/turicreate/docs/userguide/graph_analytics/intro.html)
* [Clustering](https://apple.github.io/turicreate/docs/userguide/clustering/intro.html)
* [Nearest Neighbors](https://apple.github.io/turicreate/docs/userguide/nearest_neighbors/nearest_neighbors.html)
* [Topic models](https://apple.github.io/turicreate/docs/userguide/text/intro.html)

System Requirements
-------------------

* Python 2.7 (Python 3.5+ support coming soon)
* x86\_64 architecture
* macOS 10.11+, Linux with glibc 2.12+ (including WSL on Windows 10)

Installation
------------

For detailed instructions for different varieties of Linux see [LINUX\_INSTALL.md](https://github.com/apple/turicreate/LINUX_INSTALL.md).
For common installation issues see [INSTALL\_ISSUES.md](https://github.com/apple/turicreate/INSTALL_ISSUES.md).

We recommend using virtualenv to use, install, or build Turi Create. 
Be sure to install virtualenv using your system pip.

```shell
pip install virtualenv
```

The method for installing *Turi Create* follows the
[standard python package installation steps](https://packaging.python.org/installing/).
To create a Python virtual environment called `venv` follow these steps:

```shell
# Create a Python virtual environment
cd ~
virtualenv venv
```

To activate your new virtual environment and install `Turi Create` in this environment, follow these steps:
```shell
# Active your virtual environment
source ~/venv/bin/activate

# Install Turi Create in the new virtual environment, pythonenv
(venv) pip install -U turicreate
```

Documentation
-------------

The package [User Guide](https://apple.github.io/turicreate/docs/userguide) and [API Docs](https://apple.github.io/turicreate/docs/api) contain
more details on how to use Turi Create.

GPU Support
-----------

By default, `turicreate` takes a dependency on the default installation of
`mxnet`. To enable GPU support after installation of the `turicreate` package,
please perform the following steps:

 * Install CUDA 8.0 ([instructions](http://docs.nvidia.com/cuda/cuda-installation-guide-linux/))
 * Install cuDNN 5 for CUDA 8.0 ([instructions](https://developer.nvidia.com/cudnn))

Make sure to add the CUDA library path to your `LD_LIBRARY_PATH` environment
variable.  In the typical case, this means adding the following line to your
`~/.bashrc` file:

```shell
export LD_LIBRARY_PATH=/usr/local/cuda/lib64:$LD_LIBRARY_PATH
```

If you installed the cuDNN files into a separate directory, make sure to
separately add it as well. Next step is to uninstall `mxnet` and install the
CUDA-enabled `mxnet-cu80` package:

```
(pythonenv) pip uninstall -y mxnet
(pythonenv) pip install mxnet-cu80==0.11.0
```

Make sure you install the same version of MXNet as the one `turicreate` depends
on (currently `0.11.0`). If you have trouble setting up the GPU, the [MXNet
installation instructions](https://mxnet.incubator.apache.org/get_started/install.html) may
offer additional help.
