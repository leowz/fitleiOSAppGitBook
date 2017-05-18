# Image Preview View Controller

In this controller, user can preview those taken photos to decide whether to create an avatar with those taken photos or to retake photos if he does not like any photo been taken. Once user decide to create an avatar with these photos, if he does not take face photo, the screen will segue directly to `CreatingAvatarController` , if he does take face photo then the screen will segue to `HairEyeSelectController` to select more detail for the avatar.

---

In `ImagePreviewViewController`, there are three parts of views top view, bottom view and bottom button view.

* **Top View**
  * the top view shows 3 images in a row to help user decide whether an image could be considered a good image.
* **Bottom View**
  * bottom view is the preview of all photos taken, photos can be changed horizontally by swipe gesture
* **Bottom Button View**
  * bottom button view contains two button
  * left side cancel button can present another image capture controller
  * right side confirm button can segue to the next controller which is either `CreatingAvatarViewController` or `HairEyeSelectionViewController` .

![](/assets/Pasted image at 2017_05_18 12_17 PM.jpg)

---

### Swipe Behavior

User can change the preview image by swiping left ward. Once user swipe right ward, top view image and bottom view image are changed accordingly.

// TODO: Image

---

### Animation Overlay

When `ImagePreviewViewController` are loaded and shown on screen, an animation overlay is added on the main view. This animation overlay just shows an hand image to indicate the user to use swipe gesture.

// TODO: image

---

### Mixpanel events

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen validation"\)



