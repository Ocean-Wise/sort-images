# Graphical Image Categorizer

**Dependancies:**

* Python 3.5
* Tensorflow
* Tkinter
* Numpy
* Unidecode
* Pillow
* Opencv-python

# To run:
```python3 main.py```

## Arguments:

* --labels
  * The path to the labels file to use while classifying (created by the classifier)
* --model
  * The path to the model file to use while classifying (created by the classifier)
* --input_layer
  * The name of the input layer in the model. Defaults to 'Placeholder'
* --output_layer
  * The name of the output layer in the model. Defaults to 'model'
* --images
  * The path to the directory containing the images we want to categorize

# How it works:

The application selects all JPEG images in the given directory. It then classifies the images, one at a time, with the trained *OW Image Classifier*. Each image has the option to add metadata which is written to .json files next to the images once categorized. Categorized images will be moved to a **categories** directory that contains subdirectories based on the labels fed into the classifier during training. Upon exiting and rerunning the application we first check the **categories** folder to skip the already processed images.

## Expected directory structure

The script uses globs to search for all .jpg files in the folder specified with the --images argument. It then stores their path for later processing. It is expected that all .jpg files will be siblings with their corresponding raw image files (if they exist). When the user hits the 'Next' button we copy everything in the folder that contains the .jpg into a new folder in the 'categorized' output directory.

## Tips

The Portal media server will have far too many images to classify at once. Images should be selected from the Portal server in batches and copied elsewhere for processing.

The model was trained on an OSX system and as such *may* have hardware instructions which will not be compatible with other operating systems. The model and classifying program should ideally be run on an OSX system.
