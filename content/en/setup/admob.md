---
title: Admob
description: ""
position: 15
category: Setup
---

<alert>

This step isn't required to get up and running. Feel free to jump to [run the app](/setup/app-run) section

</alert>

## Setup account

1. go to https://apps.admob.com/
2. create a new app
3. create a add unit (eg banner)
4. grab app id and ad id

## Configure Admob

### iOS

1. open `ios/App/App/Info.plist`
2. replace the string value located right below the key `GADApplicationIdentifier` to the app id obteined previously

### Android

1. open `android/app/src/main/AndroidManifest.xml`
2. open `android/app/src/main/res/values/strings.xml`
3. also add the app id to the `admob_app_id` string. it should look like

```xml
<string name="admob_app_id">YOUR_APPLICATION_ID</string>
```

### Test Device

1. on admob console go to `Settings > Test Devices`
2. add test device
3. enter a device name
4. select platform
5. add ID/IDFA. for iOS install the app `Find My IDFA`, on Android devices you can find your advertising ID in your device settings. Navigate to Settings, click Google, and then Ads.

### Client

1. open `src/app/config/admob`
2. paste add id to the variable `ADMOB_{PLATFORM}_{ADTYPE}_AD_ID`. Repeat for each AD ID variable.
3. add your ID/IDFA to `ADMOB_TESTING_DEVICES` array

> Notice: AD may take a few minutes to appear. Also keep in mind that your account must be approved by Admob team before showing ads for production.

### Learn more

- https://developers.google.com/admob/ios/quick-start?hl=en-US#import_the_mobile_ads_sdk
- https://developers.google.com/admob/android/quick-start?hl=en-US#import_the_mobile_ads_sdk
