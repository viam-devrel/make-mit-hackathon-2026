# Step 7: Capture training data
Here, you'll use your Rover's camera to capture images that will be used for your custom model. There are two ways to do this, we'll show you both so you can decide what works for your use case.

## Check your Rover's camera is working
1. Navigate back to your machines by clicking on the [**FLEET**](https://app.viam.com/fleet) tab.
1. Under the **LOCATIONS** tab, find and click on your Rover.
1. You'll be brought to the Rover's machine configuration. Find the **cam** component, which is the Rover's onboard camera.
1. Expand the **TEST** panel and confirm that your camera feed is working.

Now, you can capture training data by manually adding images to a dataset or by using a data management service.

### Manually adding images to a dataset
1. Expand your camera component's **TEST** panel. Here, you'll see the live feed of your camera as well the "Add image to dataset" icon, which looks like a camera.
   ![add current image to dataset button](/assets/addImageButton.png)
1. Using the live feed as a viewfinder, position your object fully in the frame. If needed, move your rover to get a better perspective or view of the object. The less visual clutter in the background the better!
   ![positioning a beverage for capture](/assets/positionDrink.jpeg)
   
   > 💡 **Good test data**: If you're able to set up a little "photo shoot" booth to capture images of your objects, do so! My own setup consisted of a piece of cardboard propped up by a bookend, my camera close enough to let the cardboard fill the frame, and enough space to place my object. Great images are clear, well-lit, minimize visual noise or clutter, and clearly isolate the object you are trying to capture. If possible, capturing different angles and different lighting scenarios are great additions to your dataset as well. Remember, for each object you are trying to detect, **at least 10 images** are needed to train a model!
1. When you are happy with the image, click the **Add current image to dataset** button (updated UI: it will be under the "Export screenshot" button).
   ![adding image to dataset](/assets/takeScreenshot.png)
1. In the list of datasets that appear, select the dataset you wish to add your captured image to. For example, `beverages`:
   <br>
   <img src="/assets/selectDataset.png" alt="selecting the dataset" width="450" />
1. Confirm the dataset you've selected, then click **Add**.
   <br>
   <img src="/assets/addToDataset.png" alt="add current image to selected dataset" width="450" />
1. A success message will appear at the top-right once your image is added to your selected dataset.
   <br>
   <img src="/assets/imageSaveSuccess.png" alt="successful image added to dataset" width="350" />
1. Repeat these steps to capture at least **10 images of each object** you will be detecting. Be sure to vary angles and positions!

### Alternative: Use data capture and data management service to capture images
You can use the data management service to capture data from the Rover's camera, then sync it to the cloud. 

1. Navigate to your **cam** (camera component) for your rover in **Builder** mode.
1. Find the **Data capture** section in the resource panel.
1. Click **+ Add method**.

   <img src="https://docs.viam.com/tutorials/data-management/add-method.png" alt="Disable data capture toggle" resize="800x" style="width:500px" class="shadow imgzoom" />

1. If you see a **Capture disabled on data management service** warning, click **Enable capture on data management service**.
1. Select a **Method** to capture data from.
   - **GetImages**: Returns one image for each camera sensor as a JPEG (for color sensors) or point cloud (for depth sensors).
1. Set the capture **Frequency** in hertz, for example to `0.2` with `GetImages` on a camera to capture an image every 5 seconds.
1. **Save** your config.
1. Be mindful that this can result many images! Once you have enough images for your training data (at least 10 different images of each object you are trying to detect), you can toggle the **Capturing** setting of the data capture method off to stop capturing more images. Be sure to hit save.
1. Navigate back to the **DATA** tab. Select all of the images you'd like to use for training (by checking each desired image's checkbox), then click the **Add to dataset** button.
1. Select the dataset you created earlier in this workshop. Then click **Add # images**


