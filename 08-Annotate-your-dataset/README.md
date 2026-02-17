# Step 8: Annotate your dataset
Having images to train a model is a good start. However, they won't be useful unless TensorFlow has a bit more information to work with. In this step, you'll draw bounding boxes around your objects and label them accordingly. 

To make this step easier to explain, we'll be annotating different beverages to prepare them for a custom beverage detector model. Feel free to annotate your dataset according to your own objects!

1. In [the Viam app](https://app.viam.com/data/datasets), find the **DATASETS** tab.
1. Click on the name of your dataset, for example `beverages`:
   <br>
   <img src="/assets/selectBeverages.png" alt="datasets overview" width="350" />
1. Here, you'll see all of the images you've captured, neatly grouped into its own space.
   ![beverages dataset overview](/assets/datasetOverview.png)
1. Select one image from the dataset. A side panel will appear on the right-hand side. You can see details about this image, such as any objects annotated, associated tags, which datasets the image belongs to, among other details. Click on the **Annotate** button in this panel.
   ![dataset side panel when single image selected](/assets/selectSingleImage.png)
1. The selected image opens to a larger screen. To detect an object within an image, a label must be given. Create an appropriate label for the beverage you have selected, for example `spindrift_pog`:
    ![image label creation - spindrift_pog](/assets/createLabel.png)  
1. With the appropriate label now chosen, hold the _Command_ or _Windows_ key down while you use your mouse to draw a bounding box around your beverage.
   ![gif of bounding box being drawn around drink](/assets/annotation.gif)
1. In the **OBJECTS** panel on the right, you'll see your beverage listed, with an object count of `1`. If you hover over this item, you'll see the `spindrift_pog` label appear in the image and the bounding box fill with color.
   ![drink annotated](/assets/drinkAnnotated.png)
1. Repeat this for the rest of the images that match the label. You can quickly navigate between images by pressing the `>` (right arrow) or `<` (left arrow) keys on your keyboard.
1. Once you get to a new beverage, create another descriptive label, draw the bounding box, and repeat for the rest of the images of the same beverage. Double check that each image only has one label and detects the correct beverage! _(Multiple labels and therefore, bounding boxes, are allowed and make sense for more complex detections. Since we are just trying to accurately detect the correct beverage one at a time, one label per image is recommended for this codelab)_
   ![new drink label and annotation](/assets/newLabelAnnotation.gif)
1. When you are finished annotating all of your images, you can exit out of the annotation editor by clicking on the "X" in the top-left corner. Notice that a breakdown of your bounding box labels are calculated and displayed:
   <img src="/assets/labelBreakdown.png" alt="label breakdown" width=300 />
1. Be sure that all your images are labeled, that there are no `Unlabeled` images left, and that there are at least 10 images of each beverage you are planning to detect.

Great work annotating all of that. (so..many..objects...) Your model will be the better for it. Let's finally train your custom model!