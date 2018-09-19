# DJI SDK Sample for Windows 10 and Universal Windows Platform 
![Screenshot](http://www2.djicdn.com/assets/images/products/mavic-air/banner/drone-2aa05a6dc1fd6c94dfe80f6bd4a907ba.png?from=cdnMap)

This sample is a [Universal Windows Platform](https://docs.microsoft.com/en-us/windows/uwp/get-started/universal-application-platform-guide)* app that demonstrates DJI Windows SDK capabilities: 
* Aircraft's camera video feed 
* Aircraft control (Joysticks and Takeoff/Home functionality)
* Camera gimbal control 
* Flight telemetry data events

The app leverages XAML-based UI and Windows ML, running inference (evaluation) on top of aircraft's video feed using a [Windows ML](https://docs.microsoft.com/en-us/windows/uwp/machine-learning/) model. 

![Screenshot](https://user-images.githubusercontent.com/4735184/39741103-4605c4fc-524d-11e8-92d4-0ff200b501ca.jpg)

## Windows ML ##  
This sample uses a WinML model called InkShapes. It was made by [Nikola Metulev](https://github.com/nmetulev) and trained in [Custom Vision](https://www.customvision.ai/) on simple black-and-white hand-drawn pictures representing one of 21 categories, such as house, flower, stick figure, bike, and others.

With Custom Vision, you can train an AI model using your own images, then export it to different model formats including [ONNX](https://onnx.ai). 

The model is not smart enough yet. House, flower, and stick figure are recognized quite well. 
You may help Nikola training the model - just by drawing shapes in [Draw the shape!](https://www.microsoft.com/store/productId/9NBLLH7XBRSR) app. 

## Requirements: ##
1. [Windows 10 April 2018 Update](https://www.microsoft.com/en-us/software-download/windows10).  
2. [Windows 10 SDK](https://developer.microsoft.com/en-us/windows/downloads/windows-10-sdk) 1803 (for April 2018 Update).
3. [Visual Studio 2017](https://www.visualstudio.com/vs/) with Universal Windows Platform tools (including C++ tools for UWP), Desktop C++ Development and Desktop .NET development.
4. **DJI SDK for Windows**. All BUILD 2018 attendees should have a link to DJI Windows SDK alpha. 

## How to build ## 

**You need DJI Windows SDK.**

### Prepare the SDK: ### 
DJI Windows SDK is not included in this repo. You need to obtain it from DJI, and copy 2 folders from the SDK to this project's folder. 
1. Copy **DJIWindowsSDK** folder from the SDK's package to the root of this project. 
2. Copy **ThirdParties** folder from the SDK's sample (DJIWindowsSDKDemo/ThirdParties) to the root of this project. 
![How to copy SDK folders](https://user-images.githubusercontent.com/4735184/39739976-6c716f10-5248-11e8-9466-3e88e04bea03.jpg) 

Note, these 2 folders are in .gitignore, so if you want to have them in your repo, please remove these 2 lines from .gitignore: 
```
ThirdParties/
DJIWindowsSDK/ 
```

### Build with Visual Studio 2017: ### 
1. Once you copied all required dependencies, open **WinDrone.sln** in Visual Studio 2017 
2. Right-click on **DJIUWPDemo**, click 'Set as StartUp Project' 
3. Build, debug, deploy, enjoy! 

## *Platform notes ##
Current alpha version of DJI SDK only supports x86 architecture on Windows desktop. It has a few "classic" Win32 dependencies, so the app package requires Full Trust capability (using [Desktop Bridge](https://docs.microsoft.com/en-us/windows/uwp/porting/desktop-to-uwp-extensions)), and only runs on Windows 10 Desktop. 
Video decoding component doesn't leverage hardware acceleration yet. 

The sample C# app uses the SDK via an additional DJIClient DLL and PInvoke calls. 

Full Universal Windows Platform support and other improvements are coming later towards the release of DJI Windows SDK. 


