[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-AndroidAudioRecorder-green.svg?style=true)](https://android-arsenal.com/details/1/4099) [![Release](https://jitpack.io/v/adrielcafe/AndroidAudioRecorder.svg)](https://jitpack.io/#adrielcafe/AndroidAudioRecorder)

# AndroidAudioRecorder

> A pretty way to record .WAV audio on Android

![Screenshots](https://raw.githubusercontent.com/adrielcafe/AndroidAudioRecorder/master/screenshots.png)

## How To Use

1 - Add these permissions into your `AndroidManifest.xml` and [request for them in Android 6.0+](https://developer.android.com/training/permissions/requesting.html)
```xml
<uses-permission android:name="android.permission.RECORD_AUDIO"/>
<uses-permission android:name="android.permission.WRITE_EXTERNAL_STORAGE"/>
```

2 - Open the recorder activity
```java
String filePath = Environment.getExternalStorageDirectory() + "/audio.wav";
int color = getResources().getColor(R.color.colorPrimaryDark);
int requestCode = 0;
AndroidAudioRecorder.with(this)
    .setFilePath(filePath)
    .setColor(color)
    .setRequestCode(requestCode)
    .record();
```

3 - Wait for result
```java
@Override
protected void onActivityResult(int requestCode, int resultCode, Intent data) {
    super.onActivityResult(requestCode, resultCode, data);
    if (requestCode == RECORD_AUDIO) {
        if (resultCode == RESULT_OK) {
            // Great! User has recorded and saved the audio file
        } else if (resultCode == RESULT_CANCELED) {
            // Oops! User has canceled the recording
        }
    }
}
```

## Import to your project
Put this into your `app/build.gradle`:
```
repositories {
  maven {
    url "https://jitpack.io"
  }
}

dependencies {
  compile 'com.github.adrielcafe:AndroidAudioRecorder:0.0.4'
}
```

## TODO
- [ ] Pause audio
- [ ] Play recorded audio
- [X] Tint images to black when background color is too bright

## Dependencies
* [OmRecorder](https://github.com/kailash09dabhi/OmRecorder)

## License
```
The MIT License (MIT)

Copyright (c) 2016 Adriel Café

Permission is hereby granted, free of charge, to any person obtaining a copy
of this software and associated documentation files (the "Software"), to deal
in the Software without restriction, including without limitation the rights
to use, copy, modify, merge, publish, distribute, sublicense, and/or sell
copies of the Software, and to permit persons to whom the Software is
furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in
all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR
IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY,
FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE
AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER
LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM,
OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN
THE SOFTWARE.
```
