# mnist-scikit-svm-to-coreml

## From a MNIST handwritten digit classifier to Apple's Core ML format

This tutorial goes through:
1) Loading MNIST handwritten image data
2) Training scikit-learn Support Vector Machine (SVM) model with the handwritten digit data
3) Converting scikit-learn SVM model into Apple's Core ML format
4) Loading the coreml model and testing 

## Setting Up Environment

We use coremeltools to convert scikit-learn model to coreml format: https://pypi.python.org/pypi/coremltools

Currently, coremltools is available only for python 2.7. That's why our environment is based on python 2.7.
You can use the following command to create conda environment. You just need to replace < env > with the name you prefer
for the environment name. I assume that you have anaconda installed in your system. If you do not prefer to use conda, 
instead you can get the packages that are listed in environment.txt with your favorite package manager.

````
conda create --name <env> --file environment.txt
````

After the environment is created, you can activate the environment:

````
source activate <env>
````


In the conda environment, you can use standard package management tool (pip) for python to install coremltools:

````
pip install -U coremltools
````

Now you can launch jupyter to go through the notebook. 

````
jupyter-notebook 
````

After you have done with running jupyter notebook, you can deactivate the environment:

````
source deactivate <env>
````
## Core ML format
If you have Xcode 9 installed on your system, you can see that "digit_recognizer.mlmodel" is recognized and market 
with the following icon. 

![alt text](figures/core_ml.png "")
 
You can drag and drop the following model in a Xcode project to include and use the model in your app. Or directly 
click on the open to see the model specs:

![alt text](figures/mlmodel_specs.png "")

## Notes

1. coremltools install command gave an error in the first try; however, running the command second time
fixed the issue.

2. Make sure that jupyter notebook runs in python 2 environment. mnist_loader.py uses pickle, and the way
pickle is used requires some minor changes depending on the python version 2 and 3. 
The current mnist_loader.py should work well with python 2.

3. When trying to convert scikit-learn svm model to core ml model, you might get the following error:
 
````
RuntimeError: Got non-zero exit code 72 from xcrun. Output was: xcrun: error: unable to find utility "coremlcompiler", not a developer tool or in PATH
````

In order to fix it, you need to install Xcode 9 (beta) from Apple developer site and and set the path:

````
xcode-select --print-path (check the version of xcode currently used)
sudo xcode-select --switch /Applications/Xcode-beta.app/Contents/Developer (set the path to xcode-beta)
````
