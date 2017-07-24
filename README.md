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

Now you can launch jupyter to go through the notebook:

````
jupyter-notebook 
````

After you have done with your work, you can deactivate the environment:

````
source deactivate <env>
````

## Notes

coremltools install command gave the error in the first try; however, running the command second time
fixed the issue.

