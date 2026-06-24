# Ground Truth Dataset

This repository contains the ground truth dataset for our paper **"Unveiling the Ownership: An Empirical Study of Android App Associations via SDK IDs"**, which has been accepted by **ICSME 2026**. 

The dataset provides manually verified associations of Android apps belonging to the same ownership/organization, along with their corresponding SDK IDs and metadata. This ground truth is used to evaluate the effectiveness of utilizing SDK IDs for app ownership linkage.

## Dataset Overview

The dataset consists of **118** app families/groups, a total of **542** distinct Android APK versions, and **12,239** extracted SDK IDs.

- **`Ground_Truth.tar.gz`**: The compressed archive containing all ground truth JSON files. Please unpack this file to access the data.

Once extracted, you will find the following three JSON files:

### 1. `Ground_Truth_App_Info.json`
This file groups app metadata by their respective app family.
- **Key**: App family/group identifier (e.g., `"jiakaobaodian"`).
- **Value**: A list of strings, where each string represents an app version belonging to this family. The string contains comma-separated metadata: App Label, App Name, Package Name, Version Number, Main Activity, Cert Info, Cert Serial Number, and File Name.

**Example Snippet:**
```json
{
  "jiakaobaodian": [
    "App Label: com.handsgo.jiakao.android_500081000, App Name: 驾考宝典, Package Name: com.handsgo.jiakao.android, Version Number: 500081000, Main Activity: com.handsgo.jiakao.android.splash.Login, Cert Info: countryName=CN;..., Cert Serial Number: 4e115523, File Name: 驾考宝典8.10.0.apk"
  ]
}
```

### 2. `Ground_Truth_App_MD5.json`
This file maps each unique APK to its MD5 hash for integrity verification.
- **Key**: APK File Name.
- **Value**: MD5 hash string of the APK.

**Example Snippet:**
```json
{
  "驾考宝典8.10.0.apk": "f2569c0031f43aba87d57280a02ae9f5",
  "央视新闻9.7.0.apk": "1b5a7aa5bee96a67da5d85b9997f8806"
}
```

### 3. `Ground_Truth_App_SDK_IDs.json`
This file provides the core data of our study: the SDK IDs extracted from each app.
- **Key**: APK File Name.
- **Value**: A list of strings representing various SDK IDs (e.g., SDK app keys, UUIDs, WeChat app IDs, etc.) extracted from the corresponding APK.

**Example Snippet:**
```json
{
  "驾考宝典8.10.0.apk": [
    "500659",
    "e9d20941-38ac-4c04-b496-5cfb715438b2",
    "wx6fcf65f28d6a3919",
    "appkey=7qGbHlLsXU4Ooo4CsKK0W4skS"
  ]
}
```

## How to Use

1. Download the `Ground_Truth.tar.gz` archive.
2. Unpack the archive using `tar` or any extraction tool:
   ```bash
   tar -xzvf Ground_Truth.tar.gz
   ```
3. The extracted JSON files can be easily parsed using standard JSON libraries in Python, Java, etc.
