[![Android Arsenal](https://img.shields.io/badge/Android%20Arsenal-PermissionMadeEasy-blue.svg?style=flat)](https://android-arsenal.com/details/1/7335)

PermissionMadeEasy
=======

Android Library for Easily calling Runtime Permission on Android Marshmallow and above

## How to build

Add Jitpack.io to your project level build.gradle file 
```gradle
allprojects {
    repositories {
        maven { url 'https://jitpack.io' }
    }
}
```
  
Add the dependency
```gradle
dependencies {
	  implementation 'com.github.someshkumar049:permissionmadeeasy:1.1.1'
	}
```
  
## How to use
  
Create a `PermissionHelper` object
  
```java
 PermissionHelper permissionHelper = PermissionHelper.Builder()
                .with(this)
                .requestCode(REQUEST_CODE_MULTIPLE)
                .setPermissionResultCallback(this)
                .askFor(Permission.CALENDAR, Permission.CAMERA, Permission.CONTACTS)
                .rationalMessage("Permissions are required for app to work properly") //Optional
                .build();
 ```
 and when you want to ask for the permission just call
 ```java
permissionHelper.requestPermissions();
 ```
 
Override `onPermissionsGranted` and `onPermissionsDenied` methods

Also override 

```java
@Override
    public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
        super.onRequestPermissionsResult(requestCode, permissions, grantResults);
        permissionHelper.onRequestPermissionsResult(requestCode, permissions, grantResults);
    }
```  

Detailed full sample project is included. Check [DemoActivity](https://github.com/someshkumar049/PermissionMadeEasy/blob/master/app/src/main/java/com/somesh/pemissionmadeeasy/DemoActivity.java) for full implemetation 
