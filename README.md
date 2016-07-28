# ZXing-Standalone-library

# OverView
This is the library modified from the original [ZXing Project](https://github.com/zxing/zxing). The code is not modified in any way but is just compiled into a library so that the user doesn't have to download the app separately for which you have to use [IntentIntegrator](https://github.com/zxing/zxing/blob/master/android-integration/src/main/java/com/google/zxing/integration/android/IntentIntegrator.java) to handle the app installations.

# Uses
Add the `zxing_standalone` project from the library into your project by selecting the project>New>Module>Import Gradle Project.
Send as intent when you need to scan, like on clicking on a button

    Intent intent = new Intent(getApplicationContext(),CaptureActivity.class);
                intent.setAction("com.google.zxing.client.android.SCAN");
                intent.putExtra("SAVE_HISTORY", false);
                startActivityForResult(intent, 0);

Handle the result from the intent by overriding 'onActivityResult'

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
* To compile the library yourself from the original source, follow [this step by step tutorial](http://stackoverflow.com/a/38423626/2922480)
