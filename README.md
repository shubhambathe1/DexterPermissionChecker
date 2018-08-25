# DexterPermissionChecker
Dexter is an Android library that simplifies the process of requesting permissions at runtime.

Sample Code:

    /**
     * Requesting camera permission
     * This uses single permission model from dexter
     * Once the permission granted, opens the camera
     * On permanent denial opens settings dialog
     */
    private void requestCameraPermission() {
        Dexter.withActivity(this)
                .withPermission(Manifest.permission.CAMERA)
                .withListener(new PermissionListener() {
                    @Override
                    public void onPermissionGranted(PermissionGrantedResponse response) {
                        // permission is granted
                        openCamera();
                    }

                    @Override
                    public void onPermissionDenied(PermissionDeniedResponse response) {
                        // check for permanent denial of permission
                        if (response.isPermanentlyDenied()) {
                            showSettingsDialog();
                        }
                    }

                    @Override
                    public void onPermissionRationaleShouldBeShown(PermissionRequest permission, PermissionToken token) {
                        token.continuePermissionRequest();
                    }
                }).check();
    }
    

Screen 1:

<img src="https://user-images.githubusercontent.com/31159892/44618229-a6618a00-a88f-11e8-8f76-b41167bdb916.png" width="310" height="600">

Screen 2:

<img src="https://user-images.githubusercontent.com/31159892/44618230-a8c3e400-a88f-11e8-96aa-a9b77e3c6887.png" width="310" height="600">

Screen 3:

<img src="https://user-images.githubusercontent.com/31159892/44618231-ab263e00-a88f-11e8-90c6-0971e31facb8.png" width="310" height="600">

Screen 4:

<img src="https://user-images.githubusercontent.com/31159892/44618233-acf00180-a88f-11e8-9ceb-b3105caac152.png" width="310" height="600">
