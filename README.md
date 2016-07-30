# Overview
This is the library modified from the original [ZXing Project](https://github.com/zxing/zxing). The code is not modified in any way but is just compiled into a library so that the end user doesn't have to download the scanner app separately.

# Adding the library 
Add this line (if not already present there) in the project's `build.gradle` file

    repositories {
        jcenter()
    }

Add this statement in the `dependencies` block of app's `build.gradle` file

    compile 'com.tarun0.zxing-standalone:zxing-standalone:1.0.0'

#Usage
Send an intent when you need to scan, like on clicking on a button

    Intent intent = new Intent(getApplicationContext(),CaptureActivity.class);
                intent.setAction("com.google.zxing.client.android.SCAN");
                intent.putExtra("SAVE_HISTORY", false);
                startActivityForResult(intent, 0);

Handle the result from the intent by overriding `onActivityResult`

        @Override
        protected void onActivityResult(int requestCode, int resultCode, Intent data) {
            if (requestCode == 0) {
                if (resultCode == RESULT_OK) {
                    String contents = data.getStringExtra("SCAN_RESULT");
                    Log.d(TAG, "contents: " + contents);
                } else if (resultCode == RESULT_CANCELED) {
                    Log.d(TAG, "RESULT_CANCELED");
                }
            }
        }

# Notes
* Please consider going through this answer by one of the original authors before including the app in your project, here: http://stackoverflow.com/a/9942761
* To compile the library yourself from the original source, follow [this step by step tutorial](http://stackoverflow.com/a/38423626/2922480).