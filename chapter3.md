# ImageCaptureBisController & ImageCaptureOverlayViewController

`ImageCaptureBisController` and `ImageCaptureOverlayViewController` are the controllers responsible for set up the infrastructure and perform the process of taking photos for creating an avatar. `ImageCaptureBisController` servers as a container for `ImageCaptureOverlayViewController` and `ImageCaptureOverlayViewController` are responsible for the process for taking photos.

---

## OverView

The relation between `ImageCaptureBisController` and `ImageCaptureOverlayViewController` are tricky and puzzling. We wouldn\`t ask why its was designed that way, as it was designed and implemented by different developer at different time. But what we are sure is that it can be better designed sometimes in the future.

In short, `ImageCaptureBisController` present `ImageCaptureOverlayViewController` view by adding its view to BisController\`s view as a subview. And BisController also provide some code to handling photo data for OverlayViewController. It is also responsible for start and stop the shake detection for camera and show permission alert if camera is not permitted by the user.

The workflow for image capture is simple, when the user finish the tutorial for taking photos or just skip the tutorial, the screen for image capture is shown automatically, and after user start the process of taking photos, all the steps of taking photos will be initiated one by one. 

//TODO: workflow pic here

---



