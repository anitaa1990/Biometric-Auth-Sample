# Biometric-Auth-Sample
Add Biometric Authentication to any Android app</br>

This library provides an easy way to implement fingerprint authentication without having to deal with all the boilerplate stuff going on inside.

<img src="https://img.shields.io/badge/API-23%2B-blue.svg?style=flat" style="max-width:100%;" alt="API" data-canonical-src="https://img.shields.io/badge/API-23%2B-blue.svg?style=flat" style="max-width:100%;">


<p><a href="https://github.com/anitaa1990/Biometric-Auth-Sample/blob/master/media/1.png" target="_blank"><img src="https://github.com/anitaa1990/Biometric-Auth-Sample/blob/master/media/1.png" width="250" style="max-width:100%;"></a></p>
</br></br></br>



<h2>How to integrate the library in your app?</h2>
<b>Gradle Dependecy</b></br>

```gradle
dependencies {
        implementation(group: 'com.an.biometric', name: 'biometric-auth', version: '0.1.0', ext: 'aar', classifier: '')
}
```

<h2>Usage</h2>

```
new BiometricManager.BiometricBuilder(MainActivity.this)
                        .setTitle("Add a title")
                        .setSubtitle("Add a subtitle")
                        .setDescription("Add a description")
                        .setNegativeButtonText("Add a cancel button")
                        .build()
                        .authenticate(biometricCallback);
```

The ```BiometricCallback``` class has the following callback methods:

```
new BiometricCallback() {
              @Override
              public void onSdkVersionNotSupported() {
                     /*  
                      *  Will be called if the device sdk version does not support Biometric authentication
                      */
               }

               @Override
               public void onBiometricAuthenticationNotSupported() {
                     /*  
                      *  Will be called if the device does not contain any fingerprint sensors 
                      */
               }

               @Override
               public void onBiometricAuthenticationNotAvailable() {
                    /*  
                     *  The device does not have any biometrics registered in the device.
                     */
               }

               @Override
               public void onBiometricAuthenticationPermissionNotGranted() {
                      /*  
                       *  android.permission.USE_BIOMETRIC permission is not granted to the app
                       */
               }

               @Override
               public void onBiometricAuthenticationInternalError(String error) {
                     /*  
                      *  This method is called if one of the fields such as the title, subtitle, 
                      * description or the negative button text is empty
                      */
               }

               @Override
               public void onAuthenticationFailed() {
                      /*  
                       * When the fingerprint doesn’t match with any of the fingerprints registered on the device, 
                       * then this callback will be triggered.
                       */
               }

               @Override
               public void onAuthenticationCancelled() {
                       /*  
                        * The authentication is cancelled by the user. 
                        */
               }

               @Override
               public void onAuthenticationSuccessful() {
                        /*  
                         * When the fingerprint is has been successfully matched with one of the fingerprints   
                         * registered on the device, then this callback will be triggered. 
                         */
               }

               @Override
               public void onAuthenticationHelp(int helpCode, CharSequence helpString) {
                         /*  
                          * This method is called when a non-fatal error has occurred during the authentication 
                          * process. The callback will be provided with an help code to identify the cause of the 
                          * error, along with a help message.
                          */
                }

                @Override
                public void onAuthenticationError(int errorCode, CharSequence errString) {
                         /*  
                          * When an unrecoverable error has been encountered and the authentication process has 
                          * completed without success, then this callback will be triggered. The callback is provided 
                          * with an error code to identify the cause of the error, along with the error message. 
                          */
                 }
              });

```



