# WEB SERVICE DOWNLOAD PIPELINE

This chapter is dedicated to the process of OpenGL resource download, which is the download pipeline. And structure of this pipeline is the same for download both garments resource and avatar model resource. Because the Webservice, AvatarManeger and ClothManeger class are too big to make a clear description, we only will talk about the download pipeline which is one of the most important one.

---

## Download Pipeline Work Flow

Download work flow for downloading avatar resource and garment resource is designed in a very complicated way due to years of addition of works. Here we will mainly talk about the method call stack and download progress callback.

### Avatar Download Pipeline Work Flow

Avatar download pipeline is quite similar compared with garment download pipeline. However, there is some differences due to the implementation. They call difference method obviously, however the patterns of the workflow are quite the same.

Note that there are two scenario that user this work flow which is the process of downloading avatar in creating avatar and the process of downloading avatar when user changes avatar and confirm to download. The difference is that for creating process, we need to observe the service and wait before the avatar resources are created before we can download, and for changing avatar, we just download the resource directly.

### ![](/assets/WebService_sharedService_getUserInfoAndDownloadAvatar.png)Garment Download Pipeline Work Flow

There are two places that garment download pipeline are used, when user in the home view screen to try on some garment and when the app is launched and need to download some default garment for the avatar.

![](/assets/ClothesManager_sharedManager_getSimulationClothesProgress %282%29.png)

---

### Garment Download Progress Callback

We can manage the behavior of UI from different stages of download process, and there are 4 stages of process which we can basically observe and set the callback to some code to execute during certain period of the Garment download process. And basically, there is the some process for avatar download process but there just is not any designed api to set callback closure to execute.

So there are four stages during the download pregress, which is creating, downloading ,unzipping and finished.

![](/assets/import1.png)

* creating
  * on server side simulation process, if an avatar is not pre simulated, this process will take up to 60s due to the complexity of computation. Else if simulated, this process just conform that the app can just download the resource
* download
  * start a download request from the download endpoint to retrieve the avatar model resource. This process might take 2 - 3s if the network is good enough, and might take up to 15s if the network is bad.
  * when a download is slower then 15s, no matter there is an error or not, the request will be considered a time out error. 
  * In Garment download context, time out error causes nothing and expect user to cancel download process. In avatar download context, however, an redownload alert will be raised to the user.
 



