### uCrop 导入方案



Github：https://github.com/Yalantis/uCrop



1. Include the library as local library project.

   ```
   allprojects {
      repositories {
         jcenter()
         maven { url "https://jitpack.io" }
      }
   }

   ```

   `compile 'com.github.yalantis:ucrop:2.2.1'` - lightweight general solution

   `compile 'com.github.yalantis:ucrop:2.2.1-native'` - get power of the native code to preserve image quality (+ about 1.5 MB to an apk size)

2. Add UCropActivity into your AndroidManifest.xml

   ```
   <activity
       android:name="com.yalantis.ucrop.UCropActivity"
       android:screenOrientation="portrait"
       android:theme="@style/Theme.AppCompat.Light.NoActionBar"/>

   ```

3. The uCrop configuration is created using the builder pattern.

   ```
   UCrop.of(sourceUri, destinationUri)
       .withAspectRatio(16, 9)
       .withMaxResultSize(maxWidth, maxHeight)
       .start(context);
   ```

4. Override `onActivityResult` method and handle uCrop result.

   ```
   @Override
   public void onActivityResult(int requestCode, int resultCode, Intent data) {
       if (resultCode == RESULT_OK && requestCode == UCrop.REQUEST_CROP) {
           final Uri resultUri = UCrop.getOutput(data);
       } else if (resultCode == UCrop.RESULT_ERROR) {
           final Throwable cropError = UCrop.getError(data);
       }
   }
   ```

5. You may want to add this to your PROGUARD config:

   ```
   -dontwarn com.yalantis.ucrop**
   -keep class com.yalantis.ucrop** { *; }
   -keep interface com.yalantis.ucrop** { *; }
   ```