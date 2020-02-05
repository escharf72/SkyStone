## Elisabeth Code Notes
Vuforia images research:
- use Vuforia.Image class 

### Example code
https://library.vuforia.com/articles/Solution/Working-with-the-Camera#How-To-Obtain-HD-Camera-Frames
CameraDevice.Instance.SetFrameFormat(PIXEL_FORMAT.RGB888, true); // in setup

VuforiaARController.Instance.RegisterVuforiaStartedCallback(OnVuforiaStarted);// outside of the main loop

 // Vuforia has started, now register camera image format  
    if (CameraDevice.Instance.SetFrameFormat(mPixelFormat, true))
    {
      Debug.Log("Successfully registered pixel format " + mPixelFormat.ToString());
      mFormatRegistered = true;
    }
      else
    {
      Debug.LogError(
        "Failed to register pixel format " + mPixelFormat.ToString() +
        "\n the format may be unsupported by your device;" +
        "\n consider using a different pixel format.");
    
          mFormatRegistered = false;
      }

### Imports that one of the other teams used
import android.graphics.Bitmap;
import android.graphics.Color;
import android.os.Environment;

import com.vuforia.Image;
import com.vuforia.PIXEL_FORMAT;
import com.vuforia.Vuforia;
import static android.graphics.Bitmap.createBitmap;
import static android.graphics.Bitmap.createScaledBitmap;

### Creating and storing the BitMap
Bitmap bitmap = Bitmap.createBitmap(rgbImage.getWidth(), rgbImage.getHeight(), Bitmap.Config.RGB_565);
            bitmap.copyPixelsFromBuffer(rgbImage.getPixels());

            String path = Environment.getExternalStorageDirectory().toString();
            FileOutputStream out = null;
