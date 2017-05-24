# WEB SERVICE DOWNLOAD PIPELINE

This chapter is dedicated to the process of OpenGL resource download, which is the download pipeline. And structure of this pipeline is the same for download both garments resource and avatar model resource. Because the Webservice, AvatarManeger and ClothManeger class are too big to make a clear description, we only will talk about the download pipeline which is one of the most important one.

---

## Download Pipeline Work Flow

Download work flow for downloading avatar resource and garment resource is designed in a very complicated way due to years of addition of works. Here we will mainly talk about the method call stack and download progress callback.

### Avatar Download Pipeline Work Flow

Avatar download pipeline is quite similar compared with garment download pipeline. However, there is some differences due to the implementation. They call difference method obviously, however the patterns of the workflow are quite the same.

Note that there are two scenario that user this work flow which is the process of downloading avatar in creating avatar and the process of downloading avatar when user changes avatar and confirm to download. The difference is that for creating process, we need to observe the service and wait before the avatar resources are created before we can download, and for changing avatar, we just download the resource directly.

### ![](/assets/WebService_sharedService_getUserInfoAndDownloadAvatar.png)Garment Download Pipeline Work Flow





