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

// TODO: image for preview

---

### Swipe Behavior

---

### Animation Overlay

---

### Mixpanel events



