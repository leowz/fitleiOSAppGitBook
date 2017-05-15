# ImageCaptureBisController & ImageCaptureOverlayViewController

`ImageCaptureBisController` and `ImageCaptureOverlayViewController` are the controllers responsible for set up the infrastructure and perform the process of taking photos for creating an avatar. `ImageCaptureBisController` servers as a container for `ImageCaptureOverlayViewController` and `ImageCaptureOverlayViewController` are responsible for the process for taking photos.

---

## OverView

The relation between `ImageCaptureBisController` and `ImageCaptureOverlayViewController` are tricky and puzzling. We wouldn\`t ask why its was designed that way, as it was designed and implemented by different developer at different time. But what we are sure is that it can be better designed sometimes in the future.

In short, `ImageCaptureBisController` present `ImageCaptureOverlayViewController` view by adding its view to BisController\`s view as a subview. And BisController also provide some code to handling photo data for OverlayViewController. It is also responsible for start and stop the shake detection for camera and show permission alert if camera is not permitted by the user.

The workflow for image capture is simple, when the user finish the tutorial for taking photos or just skip the tutorial, the screen for image capture is shown automatically, and after user start the process of taking photos, all the steps of taking photos will be initiated one by one.

//TODO: workflow pic here

---

### START STAGE

The start stage is the stage when the infrastructures for taking photo are set up and the controller wait for user to initiate the taking photo process by pressing the button in the middle of the screen.

There are 3 group of views on screen that are important. Top Navigation bar control buttons, outline image for front image view and camera button group, and background preview layer.

//TODO: add image for start stage.

* NavigationBar Control button
  * left cancel button to go back to the view controller who presented the current view controller
  * middle label view to indicate the current stage of the photo taking process
  * right switch camera button to switch to either front or back camera
* Outline image and camera button
  * outline image is just an image overlay between the video preview and the camera button, it just serves as an indicator for user to take photo accordingly.
  * camera button is the control for camera taking photo count down, press this button to start the count down for taking photo instead of photo immediately
* Background preview layer
  * background preview layer is a CALayer added to the layer of the controller view

---

### FIRST PHOTO

First photo stage is initiated by pressing the camera button in the start stage,  then the camera button  become a count down indicator which start the count down to take photo. The count down interval is set by `photoInterval` property. When count down finishes, `takePhoto1` is called and then second photo stage is initiated.

// TODO: First photo image

---

### SECOND PHOTO

In second photo stage, the outline image for front photo is changed to the outline image for the side photo. The count down start automatically and when it finishes, the third photo stage is initiated.

//TODO: second photo

---

### THIRD PHOTO

In third photo stage, no outline image is shown and when the count down finishes, the face photo stage is initiated.

//TODO: third photo

---

### FACE PHOTO

In face photo stage, face outline image is shown and camera button is shown at the bottom of the screen. In this stage, user can only use front camera to take face photo or user can just skip this process. And after taking or skipping face photo, the screen will segue to `ImagePreviewViewController` .

//TODO: face photo

---

### MixPanel Events

In `ImageCaptureBisController.viewDidAppear`

> FitleMixpanel.track\("app-start camera"\)



