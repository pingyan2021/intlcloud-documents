
[](id:que1)
### What should I know about licenses? 

The UGSV SDK is available in the Basic Edition and Enterprise Edition. Starting from v4.5, a license is required. The Basic Edition requires only the UGSV license (`TXUgcSDK.licence`), while the Enterprise Edition also requires the Pitu license (`YTFaceSDK.licence`). You can place the licenses into the project directory and rename them accordingly.

Starting from v4.9, the license usage was changed. You can select whether to package the license into the project. When using the license, you need to call the `setLicenceURL:key:` API to set the license URL and key.
>!SDK v4.5–4.7 does not support automatic license renewal, which is supported for v4.9 and later. SDK 4.9 is compatible with the licenses on earlier versions (you cannot pass in `null` for `url` and `key`. If needed, you can pass in a random string for them). However, the licenses on later versions cannot be used on SDK versions earlier than 4.9.


[](id:que2)
### What should I know about TXUGCPublish.h?

Starting from v4.5, `TXUGCPublish` classes were moved to the demo layer from the SDK. If you need to use such classes, you can directly drag the `VideoUpload` directory into your project.



[](id:que3)
### What should I do if an error was reported when I directly ran the demo in Xcode?

You need to select the corresponding target, as shown below:
![](https://main.qcloudimg.com/raw/4c429ae5017c7990e7bf332a4b8de0ab.png)


[](id:que4)
### What should I do if a short video shoot error was reported when I connected to Xcode for debugging?

The short video shoot error `Main Thread Checker: UI API called on a background thread` may be reported when Xcode is connected to for debugging.
![](https://main.qcloudimg.com/raw/04b272c456b0e69239c0867a8e964d7a.jpg)
This is because some APIs (generally related to UI) need to be called in the main thread. If they are not called in a main thread and `Main Thread Checker` is checked, the error will be reported.

Solution: select `Product` > `Scheme` > `Edit Scheme` > `Run` > `Diagnostics` and uncheck `Main Thread Checker`.
>?This issue has been fixed on v4.9.


[](id:que5)
### What should I do if I could not find the header file when using the SDK?

- Add the header file search path in `Build Settings` > `Search Paths` > `Header Search Paths`.
- Use the `"TXLiteAVSDK_UGC/XXX.h"` method to import the SDK header file.
- Use the `@import TXLiteAVSDK_UGC;` method to import the SDK (on v5.0 or above).

You can choose one of the above methods as needed.



[](id:que6)
### What should I do if the category methods failed to be found or the project crashed during project execution?

The SDK uses some category methods. To load them, you need to add `-ObjC` in `Build Settings` > `Linking` > `Other Linker Flags` in the project.



[](id:que7)
### What should I do if the background music set for short video shooting did not work?

1. Check whether the file exists in the background music path passed in and whether the file can be played back normally.
2. Check whether the APIs are called in the following sequence: `startCameraSimple:preview:` > `setBGM:` > `startRecord`.

>!Many APIs need to be called in a certain sequence. Otherwise, they will not work. Generally, such a requirement is specified in the comments.
For example, APIs such as `setVideoResolution:`, `setVideoBitrate:`, and `setAspectRatio:` for short video shoot can take effect only if they are set before `startRecord`.


[](id:que8)
### Can the background music set for shooting be looped?

Currently, loop playback is not supported.


[](id:que9)
### Why wasn't the completion callback returned at the time specified by `endTime` when I set the background music for shooting?

If the `endTime` is smaller than the total music file duration, in SDK 4.6 or earlier, the completion callback will be triggered only after the playback of the background music is completed. In SDK 4.7 or later, the completion callback will be triggered at the time specified by `endTime`.


[](id:que10)
### Why does it take a long time to enable the camera for the first time for shooting?

Because cold startup is used, it will take a relatively long time to enable the camera on an iPhone for the first time, even if you enable the camera through a system API.

This is because it is not suitable to enable the camera in a child thread. Tests show that it will take more time if the camera is enabled in a child thread. Moreover, if the camera is consecutively enabled and disabled in the main thread, the response delay of the child thread will also increase, degrading the user experience.


[](id:que11)
### How do I implement shooting resumption?

When the first shooting is completed, do not call `stopRecord` and `stopCameraPreview` (otherwise, the shooting will stop, and you will only be able to start a new shooting). You can call `pauseRecord`, use `TXUGCPartsManager.getVideoPathList` to get the shot video segments, and use `TXVideoJoiner.joinVideo` to compose the final video (on versions earlier than 4.5). You can also directly call `TXUGCPartsManager.joinAllParts` to compose the final video more quickly (on v4.5 or later). In this way, when you resume shooting, all the shot video segments will exist, and you can continue shooting.


[](id:que12)
### What should I do if the completion callback could not be received when short video shooting was completed?

- Check whether `stopRecord` is called. Only after `stopRecord` is called can the completion callback be returned.
- Check whether the functions are called in the main thread.



[](id:que13)
### The audio could not be recorded during shooting when I used another player to play back a video and then returned to the shooting process. What should I do?

The `AudioSession` on iOS is shared by all audio/video applications. If you use another player for playback, the `AudioSession` will be occupied. If `AudioSession` is not released at all or not promptly released when the playback ends, the `AudioSession` of the shooting module will become invalid. The SDK provides two APIs: `-(void) pauseAudioSession` and `-(void) resumeAudioSession`. You can call `pauseAudioSession` first before you use another player for preview and then call `resumeAudioSession` before you continue the shooting.



[](id:que14)
### What should I do if the shot video is blurry?

The shot video will be blurry if the bitrate and resolution do not match. You can increase the bitrate accordingly and enable the B-frame feature to improve the image quality.



[](id:que15)
### What should I do if the video failed to be generated after I switched the application to the background and then to the foreground during video editing?

Hardware encoding (featuring higher encoding efficiency and image quality) is used by default for video generation. However, the hardware encoder will stop running if the application is switched to the background, resulting in video generation failure. The SDK provides two APIs: `pauseGenerate` and `resumeGenerate`. When the application is switched to the background, you can call `pauseGenerate` to pause video generation. When the application returns to the foreground, you can call `resumeGenerate` to resume video generation.

>!If `resumeGenerate` is called, the SDK will restart the hardware encoder, which may fail. Plus, the hardware encoder may fail to encode the first several frames after restarting. In this case, the SDK will throw the `TXVideoGenerateListener` error event internally, and the video will need to be generated again after the error event is received.



[](id:que16)
### What should I do if file upload failed?

The file upload status codes are as detailed below:

![](https://main.qcloudimg.com/raw/fd39ad5be960bc3988b4801181e37bf3.png)
1. Check whether the file to be uploaded is in the local sandbox. If you want to upload a file in the media library, you need to copy it to the local sandbox first.
2. If error code 1002 is returned, the signature has an exception, the timestamp has expired, or the VOD service has an exception (unactivated or suspended).
3. If error code 1003 is returned, a request parameter has an exception or the format of the file to be uploaded is not supported.



[](id:que17)
### Does short video shooting support photo capturing?

The UGSV SDK supports photo capturing. You can simply call the `snapshot` API of the `TXUGCRecord` class to get an image after the preview starts.


