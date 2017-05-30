# Home View Controller

`HomeViewController` is the principle stage of the app. It is responsible for presenting the 3D avatar model to the user, interacting with the user and managing garment action for the avatar.

---

## Overview

Home View Screen is controlled by `HomeViewController` object which is a subclass of `ViewController`\(UIViewController with small changes\). `HomeViewController`s content view controller and its view are actually populated by `ModelViewController` which is the subclass of `GLKViewController` that are responsible for presenting OpenGL ES content. This indicate that the main task for `HomeViewController` is to present content of 3D model to the user.

According to the current pipeline of 3D model, there are two modes of interaction with the avatar in home view screen:

* **Basic interactions with the 3D model of avatar**
  * Touch interactions including scaling, rotation, moving up or down of avatar.
* **Clothes mode**

  * Clothes bar and side bar are shown.
  * User can chose different garments and try on these garments on the avatar.
  * In the side bar panel user can access the stretching mode which shows the fitness of any garment on the avatar.

**Basic work flow:**

![](/assets/Pasted image at 2017_05_09 06_03 PM 2.jpg)

---

### Basic interactions

> ### ![](/assets/Pasted image at 2017_05_12 10_54 AM.png)

Here is a general screen of basic screen. There are generally 4 parts of functional components in this screen.

* **Navigation Bar **
  * Navigation Bar in the top composed of title and a button to show side menu bar.
* **ModelViewController**
  * Added as the main view of the `HomeViewController` itself. 
  * Touch events like pin,rotate and pan are predefined to interact with the avatar.
* **Side Button Panel**
  * First button to switch to clothes mode
  * Second button to create avatar by measurment 
  * Third button to create a new avatar
* **Share Button at The Right Bottom Side of The View**
  * Launch `UIActivityViewController` for share events

### NavigationBar

NavBar is preset in `viewDidLoad` method. Title view is set to Fitle title theme and menu button is set to bind `showMenuAction` method in HomeViewController.

### ModelViewController

`ModelViewController` is preset in `viewDidLoad` method. It is initialized from nib file and is added as the child view controller of `HomeViewController` and its view are set to the view of `HomeViewController`.

`ModelViewController` is a subclass of `GLKViewController`. And 4 gesture are added as a default properties.

### Side Button Panel

There are three buttons in the side button panel. `clothesButton`  button is bind with `clothesAction` action which turns the controller into clothes mode.

`measurementsButton` button is bind with `measurementsAction`  action which perform a controller transition to `AvatarMeasurementsViewController`

`settingsButton`  button is bind with `settingsAction`  action which shows the alert to let the user to confirm to transit  to `ChangeInformationViewController` to create new avatar.

### Share Button

`shareButton` button in the right bottom of the view is bind with `shareAction` action which launch the `UIActivityViewController`.

---

### Clothes Mode

> ![](/assets/Pasted image at 2017_05_12 11_00 AM.png)

User touch `clothesButton`  button to transit to clothes mode. In clothes mode, side button panel at right side of the screen changes to clothes side button panel with new buttons. Also in this mode, clothes panel in the bottom is enabled.

* **Clothes Side Button Panel**

  * New buttons that are enabled including `takeoffButton` button, `stretchingMapButton` button, `clothesInfoButton` button, `buyClothes` button.

* **Clothes panel**

  * Three collection views are included, `clothesTypeCollectionView` view, `clothesCollectionView` view, `sizeCollectionView` view.

### Clothes Side Button Panel

`takeoffButton` button is bind with `takeoffClothes` action. When an avatar has a garment on, this button is enabled and user can take on and off clothes as long as he does not initiate other clothes actions.

`stretchingMapButton` button is bind with `stretchingAction` action. When user touches this button, the avatar clothes will turn into stretching mode which shows user the comfort information of that clothes.

> ![](/assets/Pasted image at 2017_05_10 12_32 PM.png)

`clothesInfoButton` button is bind with `clothInfoAction` action. When user presses this button, Cloth info view will appear on the screen.

> ![](/assets/Pasted image at 2017_05_10 02_36 PM.png)

`buyClothes` button work the same way as the `buyClothes` button in Clothes info view does. They are bind to `buyClothAction` action. When the clothes on the avatar has a URL to a product page, then the button will be enabled and by pressing on the button, a browser will be launched and redirect the user to the product page of the current clothes on the avatar.

### Clothes Panel

There are three sections in the Clothes panel and each section is a customized collection view. All the  behaviors of the collection views are delegated in the delegation methods.

* **Clothes type collection view**
  * Situated at the bottom of clothes panel, composed of arrow button at the left and clothes type buttons at the right side of arrow button.
  * When any item cell, which is a certain type of clothes, is pressed by the user, clothes collection view will show up.
* **Clothes collection view**
  * Situated at the middle of clothes panel, with each collection item cell represents a model of clothes.
  * When item cell is pressed, the avatar will try on this clothes of recommended size. And size collection view will show up on top of clothes collection view.
* **Size collection view**

  * Situated at the top of the clothes panel, with each item cell represents a certain size of a selected clothes.

  * when cell is pressed, if the size is on then do nothing, else try on the size been pressed.

When user press the clothes collection view item, which is a certain clothes, or size collection view item, which is a certain size, the try on clothes process `tryCloth()` is triggered. And a clothes info preview view will be displayed to the user.

> ![](/assets/Pasted image at 2017_05_10 02_45 PM.png)

Related informations will be shown on the view including size and recommendation size. Try on cloth can be cancelled by press cancel button in the clothes info preview view. `cancelButton` button is bind with `undoSimulation()` action and by pressing `cancelButton` the whole try on pipe line will be cancelled.

---

## MixPanel Events

In `viewDidAppear()`

> **FitleMixpanel.track\("app-start screen home"\)**

In `measurementsAction()`

> **FitleMixpanel.track\("app - click on measurment"\)**

In `shareAction()`

> **FitleMixpanel.track\("app - click on share avatar"\)**
>
> **FitleMixpanel.track\("app - click on share on facebook"\)**
>
> **FitleMixpanel.track\("app - click on share on twitter"\)**
>
> **FitleMixpanel.track\("app - click on share with mail"\)**
>
> **FitleMixpanel.track\("app - click on share with facebook messenger"\)**

In `buyClothAction()`

> **FitleMixpanel.track\("app - click on go to product page\_tryon"\)**

In `undoSimulation()`

> **FitleMixpanel.track\("app-cancel tryon"\)**

In `clothesAction()`

> **FitleMixpanel.track\("app-start screen tryon"\)**



