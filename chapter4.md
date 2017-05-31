# Image Preview View Controller

In this controller, user can preview those taken photos to decide whether to create an avatar with those taken photos or to retake photos if he does not like any photo been taken. Once user decide to create an avatar with these photos, if he does not take face photo, the controller will segue directly to `CreatingAvatarController` , if he does take face photo then the controller will segue to `HairEyeSelectController` to select more details for the avatar.

---

## Overview

In `ImagePreviewViewController`, there are three parts of views top view, bottom view and bottom button view.

* **Top View**
  * The top view shows 3 images in a row to help user to decide whether a photo could be considered a good photo.
* **Bottom View**
  * bottom view is the preview of all photos taken, photos can be changed horizontally by swipe gesture
* **Bottom Button View**
  * bottom button view contains two button
  * left side `cancelButton` button can present another image capture controller
  * right side `validationActionButton` button will show alerts to let user confirm that he wants to use those photos to create avatar. Once confirmed, the current controller will segue to the next controller which is either `CreatingAvatarViewController` or `HairEyeSelectionViewController` .

![](/assets/Pasted image at 2017_05_18 12_17 PM.jpg)

---

### Swipe Behavior

User can change the preview image by swiping left ward. Once user swipes right ward, top view image and bottom view image will change accordingly.

![](/assets/Pasted image at 2017_05_18 02_46 PM.png)

---

### Animation Overlay

When `ImagePreviewViewController` is loaded and shown on screen, an animation overlay is added on the main view. This animation overlay just shows an hand image to indicate the user to use swipe gesture.

![](/assets/Pasted image at 2017_05_18 02_51 PM.png)

---

### Mixpanel events

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen validation"\)



