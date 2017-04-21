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

      ![](/assets/Simulator Screen Shot 20 Apr 2017, 10.48.28.jpg)















