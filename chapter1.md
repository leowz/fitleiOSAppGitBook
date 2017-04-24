# Home View Screen

Home View Screen is the principle stage of the app. It is responsible for presenting the 3D model avatar to the user,interaction with the user and managing garment action for avatar.

---

## Overview

Home View Screen is controlled by HomeViewController object in the project and subclass of ViewController\(UIViewController with small changes\). HomeViewController\`s content view controller and view is actually populated by ModelViewController which is the subclass of GLKViewController that are responsible for presenting OpenGL ES content. This indicate that the main task for Home View Screen is to present content of 3D model.

From the current pipeline of presenting 3D model, there are two modes of interaction with the avatar in home view screen:

* Basic interactions with the 3D model of avatar
  * Touch interactions including scaling, rotation, moving up or down of avatar.
* Clothes mode

  * Clothes bar and side bar are shown.
  * User can chose different garments and try on them on the avatar.
  * In the side bar panel user can access the stretching mode which shows the fitness of any garment on the avatar.

---

### Basic interactions

> ### ![](/overview.jpg)

Here is a general screen of basic screen. There are generally 4 parts of functional components in this screen.

* Navigation Bar 
  * Navigation Bar in the top composed of title and a button to show side menu bar.
* ModelViewController
  * Added as the main view of the HomeViewController itself. 
  * Touch events like pin,rotate and pan are predefined to interact with the avatar.
* Side Button Panel
  * First button to switch to clothes mode
  * Second button to create avatar by measurment 
  * Third button to create a new avartar
* Share Button at The Left Bottom Side of The View
  * Launch UIActivityViewController for share events

### NavigationBar

NavBar is preset in `viewDidLoad` method. Title view is set to Fitle title theme and menu button is set to bind `showMenuAction` method in HomeViewController.

### ModelViewController

ModelViewController is preset in `viewDidLoad` method. It is initialized from nib file and is added as the child view controller of HomeViewController and its view are set to the view of HomeViewController.

ModelViewController is a subclass of GLKViewController. And 4 gesture are added as a default properties.

### Side Button Panel

There are three buttons in the side button panel. ClothesButton is bind with `clothesAction` which turns the controller into clothes mode.

MeasurementsButton is bind with `measurementsAction` which perform a controller transit to `AvatarMeasurementsViewController`

SettingsButton is bind with `settingsAction` which shows the alert to let the user to confirm to transit  to ChangeInformationViewController to create new avatar.

### Share Button

Share Button in the right bottom of the view is bind with `shareAction` which launch the UIActivityViewController.

---

### Clothes Mode

> ![](/clothMode.jpg)

User touch Clothes Button to transit to clothes mode. In clothes mode, side button panel at right side of the screen changes to clothes side button panel, with new buttons. Also in this mode, clothes panel in the bottom is enabled.

* Clothes Side Button Panel
  * For new buttons are enabled. takeoff clothes button, stretching mode button, clothes info button, buy clothes button.
* Clothes panel

  * Three collection views are included, clothes type collection view, clothes collection view, size collection view.

### Clothes Side Button Panel

Takeoff clothes button is bind with `takeoffClothes`. When an avatar have a clothes on, this button is enabled and user can take on and off clothes as long as he does not initiate other actions.

Stretching map button is bind with `strethcingAction`. When user press this button, the avatar clothes will turn into stretching mode which shows user the comfort information of that clothes.

> ![](/comfortMode.jpg)

Clothes info button is bind with `clothInfoAction`. When user press this button, Cloth info view will appear on the screen. 

> ![](/clothInfo.jpg)

Buy clothes button work the same way as the buy button in Clothes info view does. They are bind to buyClothAction. When the clothes currently on the avatar has a URL to the product page, then the button will be enabled and by pressing on the button, a browser will be launched and redirect to the product page on the current clothes on the avatar.





