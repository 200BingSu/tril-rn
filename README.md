# Splash Screen (시작화면)

- https://til-choonham.tistory.com/530
- https://github.com/crazycodeboy/react-native-splash-screen
- https://www.npmjs.com/package/react-native-splash-screen

```bash
npm i react-native-splash-screen
```

## andorid (MainActivity.java) 수정

- android/app/src/main/java/com/앱이름/MainActivity.java
- 아래 소스는 참조만 하고 추가된 소스만 별도로 작성

```java
package com.rntil;

// 추가된 소스
import android.os.Bundle; // here

import com.facebook.react.ReactActivity;
import com.facebook.react.ReactActivityDelegate;
import com.facebook.react.defaults.DefaultNewArchitectureEntryPoint;
import com.facebook.react.defaults.DefaultReactActivityDelegate;

// 추가된 소스
// react-native-splash-screen >= 0.3.1
import org.devio.rn.splashscreen.SplashScreen; // here


public class MainActivity extends ReactActivity {

  /**
   * Returns the name of the main component registered from JavaScript. This is used to schedule
   * rendering of the component.
   */
  @Override
  protected String getMainComponentName() {
    return "rntil";
  }

  /**
   * Returns the instance of the {@link ReactActivityDelegate}. Here we use a util class {@link
   * DefaultReactActivityDelegate} which allows you to easily enable Fabric and Concurrent React
   * (aka React 18) with two boolean flags.
   */
  @Override
  protected ReactActivityDelegate createReactActivityDelegate() {
    return new DefaultReactActivityDelegate(
        this,
        getMainComponentName(),
        // If you opted-in for the New Architecture, we enable the Fabric Renderer.
        DefaultNewArchitectureEntryPoint.getFabricEnabled());
  }

  // 추가된 소스
  @Override
  protected void onCreate(Bundle savedInstanceState) {
      SplashScreen.show(this);  // here
      super.onCreate(savedInstanceState);
  }

}
```

## splash screen 용 이미지 필요

- `900 * 900` : png 파일 추천
- launch_screen.png
- android/app/src/main/res/drawable/ 저장
- android/app/src/main/res/drawable/launch_screen.png

## launch_screen.xml 파일 생성 및 배치

- android/app/src/main/res/layout 폴더 생성
- android/app/src/main/res/layout/launch_screen.xml 파일 생성

```xml
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:orientation="vertical" android:layout_width="match_parent"
    android:layout_height="match_parent">
    <ImageView android:layout_width="match_parent" android:layout_height="match_parent" android:src="@drawable/launch_screen" android:scaleType="centerCrop" />
</RelativeLayout>
```

# colors.xmal 파일 생성 및 배치

- - android/app/src/main/res/values/colors.xml

```xml
<?xml version="1.0" encoding="utf-8"?>
<resources>
    <color name="primary_dark">#000000</color>
</resources>
```

## app.tsx에 적용
