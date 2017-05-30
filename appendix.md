# All MixPanel Events

All mixpanel events are summarized below. And they are organized in sections consisted with a bold heading indicating in which controller are there these events, and followed with these events groups in this controller. Events are grouped based on the methods or functions they are in. And there usually is one line of text above each group of events indicating which method these events are in, with sometimes another line of description about this method.

---

In `HomeViewController` screen when user press the menu button on the Navigation Bar, `MenuViewController` shows up and user could select any button on the controller view to segue to the next controller.

### ConceptViewController

In `MenuViewController` , when user press `ABOUT FITLE` button, `ConceptViewController` will present to user.

**In **`ViewDidAppear`

> FitleMixpanel.track\("app-start screen about us"\)

**In **`rateAppAction`

> FitleMixpanel.track\("app - click on rate\_about"\)

**In **`likePageAction`

> FitleMixpanel.track\("app - click on like facebook"\)

**In **`legalConditionsAction`

> FitleMixpanel.track\("app - click on CGAs\_about"\)

**In **`feedbackAction`

> FitleMixpanel.track\("app - click on feedback\_about"\)

### PartnersNewViewController

In `MenuViewController` , press `PARTNER BRNADS` to present this controller.

**In **`viewDidAppear`

> FitleMixpanel.track\("app-start screen partner"\)

**In **`collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath)`

There are two group of marks in this collectionView, interchangeable by a segmented control. Touch on different group of mark will trigger different events.

> FitleMixpanel.track\("app - click on partner tryon", property:  \["url": url!\]\)
>
> FitleMixpanel.track\("app - click on partner reco", property:  \["url": url!\]\)

### FAQViewController

In `MenuViewController` , press `FAQ` button to present this controller.

**In **`viewDidAppear`

> FitleMixpanel.track\("app-start screen FAQ"\)

### ProfileViewController

In `MenuViewController` , press `MY PROFILE` button to present this controller.

**In **`viewDidAppear`

> FitleMixpanel.track\("app - click on profile infos"\)

**In **`saveAction`

In `saveAction` method, depends on what content user have changed, different events will be sent.

> FitleMixpanel.track\("app - click on update profile infos\_any"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account name"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account mail"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account birthdate"\)

### ChangePasswordViewController

In `ProfileViewController` if user want to change password,  press `Change password` text field to present this controller.

In `doneAction`

> FitleMixpanel.track\("app - click on change account password"\)

### MyAvatarsViewController

In `MenuViewController` , when user touches `MY AVATARS` button, this controller will be presented.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen my avatars"\)

In `editAvatarNameButtonAction`

> FitleMixpanel.track\("app - click on confirm change name avatar"\)

In `loadAvatarButtonAction`

Triggered when user confirms to change their current avatar.

> FitleMixpanel.track\("app-change my avatar", property: \["session\_id": self.allAvatars\[self.lastChecked\].id\]\)

In `errorMessage`

Triggered when any error occurs during avatar download process.

> FitleMixpanel.track\("app-retry download"\)

### SettingsViewController

In `MenuViewController` , when user touches `SETTINGS` button, this controller will be presented.

In `viewWillAppear`

> FitleMixpanel.track\("app-start screen settings"\)

---

### HomeViewController

This is the main stage for the app, and for presenting avatars and garments for user.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen home"\)

In `measurementsAction`

Triggered by click on the measurement button on home screen.

> FitleMixpanel.track\("app - click on measurment"\)

In `shareAction`

Different events are triggered by different share action. If user have shared successfully,  based on the application he shared on, different event will be sent.

> FitleMixpanel.track\("app - click on share avatar"\)
>
> FitleMixpanel.track\("app - click on share on facebook"\)
>
> FitleMixpanel.track\("app - click on share on twitter"\)
>
> FitleMixpanel.track\("app - click on share with mail"\)
>
> FitleMixpanel.track\("app - click on share with facebook messenger"\)

In `buyClothAction`

> FitleMixpanel.track\("app - click on go to product page\_tryon"\)

In `undoSimulation`

Triggered when user cancels the clothes downloading process.

> FitleMixpanel.track\("app-cancel tryon"\)

In `clothesAction`

Triggered when segued to clothes mode.

> FitleMixpanel.track\("app-start screen tryon"\)

In `takeoffClothes`

> FitleMixpanel.track\("app-click on remove clothes"\)

In `stretchingAction`

> FitleMixpanel.track\("app-click on stretching map"\)

In `tryCloth(:::)`

When app launches with default clothes and the clothes need to be downloaded. This method will be called and event will be sent.

> FitleMixpanel.track\("app-tryon loaded"\)

In `tryCloth()`

When user trys on any clothes from cloth mode, by touching on any garment, events below will be sent.

> FitleMixpanel.track\("app-start tryon", property: \["cloth\_id": clothChosen!, "size\_id": sizeChosen!, "color\_id": colorChosen!\]\)
>
> FitleMixpanel.track\("app-tryon loaded"\)

In `iRateUserDidAttemptToRateApp`

Triggered when the iRate panel appears and user try to rate.

> FitleMixpanel.track\("app - click on rate\_popup"\)

### AvatarMeasurementsViewController

In `HomeViewController`, when the user touches the measurements button, this controller will be presented.

In `editButtonAction`

> FitleMixpanel.track\("app - started edit measurment"\)

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen measurements"\)

In `beforeSendEmailAlert`

User tries to send measurement by email.

> FitleMixpanel.track\("app - click on send measurment by email"\)

### AvatarMeasurementDescriptionViewController

In `AvatarMeasurementsViewController`, in the list of measurements, when user touches any row of measurement, this controller will be presented to the user.

In `editButtonAction`

> FitleMixpanel.track\("app - started edit measurment"\)

---

### EditMeasurementsViewController

The controller that can create avatar from measurements.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen measurements edition"\)

In `createNewAvatarButtonAction`

> FitleMixpanel.track\("app - click on update measurment"\)

### ChangeInformationVC

This controller is the controller for user to create the first avatar. It only appears when user do not have any avatar.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen infos avatar"\)

### AvatarVideoTutorialViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen video tutorial"\)

In `skipAction`

User skips tutorial video.

> FitleMixpanel.track\("app-skip video"\)

### ImagePreviewViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen validation"\)

### ImageCaptureBisViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start camera"\)

### HairEyeSelectController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen hair eye"\)

### CreatingAvatarViewController

Its the controller that shows the avatar creation progress on server side. It appears when user finishes their photos and confirms to create the avatar.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen congratulations"\)

In `showCreationError`

When an error appears in avatar creation, user can either cancel avatar creation or recreate avatar.

> FitleMixpanel.track\("app-cancel recreate avatar"\)
>
> FitleMixpanel.track\("app-recreate avatar"\)

In `seeAvatarAction`

When an avatar are created successfully, user can click see avatar button to segue to `homeViewController`.

> FitleMixpanel.track\("app-click to see avatar"\)

### OnboardingViewController

There are two on boarding controller, that show the user the accepted way to take photos for avatar creation.

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen first onboarding"\)

### OnboardingTwoViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen second onboarding"\)



