# All MixPanel Events

---

### ConceptViewController

In `ViewDidAppear`

> FitleMixpanel.track\("app-start screen about us"\)

In `rateAppAction`

> FitleMixpanel.track\("app - click on rate\_about"\)

In `likePageAction`

> FitleMixpanel.track\("app - click on like facebook

In `legalConditionsAction`

> FitleMixpanel.track\("app - click on CGAs\_about"\)

In `feedbackAction`

> FitleMixpanel.track\("app - click on feedback\_about"\)

### PartnersNewViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen partner"\)

In `collectionView(_ collectionView: UICollectionView, didSelectItemAt indexPath: IndexPath)`

> FitleMixpanel.track\("app - click on partner tryon", property:  \["url": url!\]\)
>
> FitleMixpanel.track\("app - click on partner reco", property:  \["url": url!\]\)

### FAQViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen FAQ"\)

### ProfileViewController

In `viewDidAppear`

> FitleMixpanel.track\("app - click on profile infos"\)

In `saveAction`

> FitleMixpanel.track\("app - click on update profile infos\_any"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account name"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account mail"\)
>
> FitleMixpanel.track\("app - click on update profile infos\_changed account birthdate"\)

### ChangePasswordViewController

In `doneAction`

> FitleMixpanel.track\("app - click on change account password"\)

### MyAvatarsViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen my avatars"\)

In `editAvatarNameButtonAction`

> FitleMixpanel.track\("app - click on confirm change name avatar"\)

In `loadAvatarButtonAction`

> FitleMixpanel.track\("app-change my avatar", property: \["session\_id": self.allAvatars\[self.lastChecked\].id\]\)

In `errorMessage`

> FitleMixpanel.track\("app-retry download"\)

### SettingsViewController

In `viewWillAppear`

> FitleMixpanel.track\("app-start screen settings"\)

---

### HomeViewController

In `viewDidAppear`

> FitleMixpanel.track\("app-start screen home"\)

In `easyTipViewDidDismiss`

> FitleMixpanel.track\("app - click on measurment"\)

In `shareAction`

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

> FitleMixpanel.track\("app-cancel tryon"\)

In `clothesAction`

> FitleMixpanel.track\("app-start screen tryon"\)

In `takeoffClothes`

> FitleMixpanel.track\("app-click on remove clothes"\)

In `stretchingAction`

> FitleMixpanel.track\("app-click on stretching map"\)

In `tryCloth(:::)`

> FitleMixpanel.track\("app-tryon loaded"\)

In `tryCloth()`

> FitleMixpanel.track\("app-start tryon", property: \["cloth\_id": clothChosen!, "size\_id": sizeChosen!, "color\_id": colorChosen!\]\)
>
> FitleMixpanel.track\("app-tryon loaded"\)

In `iRateUserDidAttemptToRateApp`

> FitleMixpanel.track\("app - click on rate\_popup"\)







