# WEB SERVICE DOWNLOAD PIPELINE

This chapter is dedicated to the process of Avatar resource download, that is to say, the download pipeline. The structure of this pipeline is very similar for download garments resource and avatar model resource. Since these class Webservice, AvatarManeger and ClothManeger are too big to make a clear description, we only will talk about the download pipeline which is one of the most important one.

---

## Download Pipeline Work Flow

Download work flow for downloading avatar resource and garment resource is designed in a very complicated way due to years of addition of works. Here we will mainly talk about the method call stack and download progress callback.

### Avatar Download Pipeline Work Flow

Avatar download pipeline is quite similar compared with garment download pipeline. However, there are some differences due to the implementation. They call different methods obviously, otherwise the pattern for each workflow is quite the same.

Note that there are two scenarios that user use this work flow, that is the process of downloading avatar resource is applied either after user creates an avatar or user changes his avatar. The difference is, in creating process we need to observe the server, by polling, and wait before the avatar resources are created before we can download, in the other hand, in changing avatar we just download these resources directly.

### ![](/assets/WebService_sharedService_getUserInfoAndDownloadAvatar.png)Garment Download Pipeline Work Flow

There are two scenarios that garment download pipeline are used, when in the `homeViewController`   user tries on some garments, or when the app is launched and needs to download some default garments for the avatar.

![](/assets/ClothesManager_sharedManager_getSimulationClothesProgress %282%29.png)

---

### Garment Download Progress Callback

In garment download pipeline, there are additional progress callbacks, compared with avatar download process. By using those progress callback, we can have an higher level abstraction for the whole process and have an easier control over it.

So there are four stages during the download pregress, which is creating, downloading ,unzipping and finished.

**Callback Sequence:**

![](/assets/flow.png)

**Explanation:**![](/assets/table4.png)

