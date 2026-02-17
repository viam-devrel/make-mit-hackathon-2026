# Step 9: Train your custom model

1. In your dataset overview, click **Train model** located within the left-hand panel.
   <img src="/assets/trainModelButton.png" alt="train model button" width=400 />
1. Select your model training options. For now, leave the default selections of **New model** and **Built-in (TensorFlow Lite)**. Confirm that the correct dataset is selected. Click **Next steps**.
   ![train a model options](/assets/modelTrainingOptions.png)
1. Give your model a name, for example `beverage-detector`
   <img src="/assets/nameYourModel.png" alt="naming your custom model" width=350 />
1. Select **Object detection** as the Task type. Notice that the labels you've created are auto-detected from the images in your dataset and selected in the **Labels** section:
   ![custom model task type and labels](/assets/chooseTaskType.png)
1. Click **Train model**. This will kick off the training job for your custom model.
   ![training job in progress](/assets/trainingJobInProgress.png)
1. If you click on the **ID** of your training job, you can view more details on the job's overview. You can view any relevant logs while the job runs. 
   ![training job overview](/assets/trainingJobOverview.png)
1. Wait until your training job is complete. It may take up to 15 minutes, so feel free to take a break and stretch! Once it is finished, you'll see the status of your job change to **Completed**
   ![training job complete](/assets/trainingJobComplete.png)

Well done, you've just created your own custom model tailored to detect your specified objects! Let's add it to our machine.