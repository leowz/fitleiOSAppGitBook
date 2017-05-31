# Image Capture Bis Controller & Image Capture Overlay View Controller

`ImageCaptureBisController` and `ImageCaptureOverlayViewController` are the controllers responsible for setting up the infrastructure and performing the process of taking photos for creating an avatar. `ImageCaptureBisController` servers as a container for `ImageCaptureOverlayViewController` and `ImageCaptureOverlayViewController` are responsible for the process for taking photos. To better understand the behavior of these controllers, its better to have some basic knowledge on `AVFoundation` framework and `CALayer` class.

---

## Overview

The relation between `ImageCaptureBisController` and `ImageCaptureOverlayViewController` are tricky and puzzling. We wouldn\`t discuss why was it designed that way, as it was implemented by different developers at different times. But what we are sure is that it can and should be better designed sometimes in the future.

In short, `ImageCaptureBisController` present `ImageCaptureOverlayViewController` view by adding its view to BisController\`s view as a subview. And BisController also provide some code to handling data of photos for OverlayViewController. It is also responsible for start and stop the shaking detection for camera and show permission alert if the app has no permission to access camera yet.

The workflow for image capture is simple, when the user finishes the tutorial for taking photos or just skip the tutorial, the screen for image capture will be shown automatically, and after user starts the process of taking photos, all the steps of taking photos will be initiated one by one.

![](/assets/Pasted image at 2017_05_17 11_25 AM.jpg)

---

### START STAGE

The start stage is the stage when the infrastructure for taking photo is set up and the controller waits for user to initiate the taking photo process by pressing the button in the middle of the screen.

There are 3 groups of views on screen that are important. Top Navigation bar control buttons, outline images for front image view and camera button group, and background preview layer.

![](/assets/Pasted image at 2017_05_17 11_59 AM.png)

* **Navigation Bar Control button**
  * Left side `cancelButton` button functions to go back to the view controller who presented the current view controller
  * Middle label view indicates the current stage of the photo taking process
  * Right side `switchCameraView` button switches to either front or back camera
* **Outline Image and Camera Button**
  * Outline image is just an image overlay between the video preview and the `cameraButton` button, it just serves as an indicator for user to take photo accordingly.
  * `cameraButton` button is the control for taking photo count down, presses this button to start the count down for taking photo instead of photo immediately
* **Background Preview Layer**
  * Background preview layer is a CALayer added to the layer of the controller view

---

### FIRST PHOTO

First photo stage is initiated by pressing the `cameraButton` button in the start stage,  then the `cameraButton` button become a count down indicator who starts to count down to take photos. The count down interval is set by `photoInterval` property. When count down finishes, `takePhoto1` is called and then second photo stage is initiated. The count down process can be stopped by shake detector. If the process is stopped during any stage it can only be restarted from the first stage.

![](/assets/Pasted image at 2017_05_17 02_40 PM.png)

---

### SECOND PHOTO

In second photo stage, the outline image for front photo is changed to the outline image for the side photo. The count down start automatically and when it finishes, the third photo stage is initiated.

![](/assets/Pasted image at 2017_05_17 02_47 PM.png)

---

### THIRD PHOTO

In third photo stage, no outline image is shown and when the count down finishes, the face photo stage is initiated.

![](/assets/Pasted image at 2017_05_17 02_50 PM.png)

---

### FACE PHOTO

In face photo stage, face outline image is shown and `cameraButton` button is shown at the bottom of the screen. In this stage, user can only use front camera to take face photo, or user can just skip this process. And after taking or skipping face photo, the controller will segue to `ImagePreviewViewController` .

![](/assets/Pasted image at 2017_05_17 03_02 PM.png)

---

### MixPanel Events

In `ImageCaptureBisController.viewDidAppear`

> FitleMixpanel.track\("app-start camera"\)



