# AR_book_cover

Unity software to create an augmented reality book cover for J.R.R. Tolkein's The Fellowship of the Ring.
This program tracks the front cover and overlays a 3-D depiction of the illustration, along with title and author name. 
The program also tracks the back cover and overlays revelant publication information. On the back cover, there is an augmented reality "See Review" push putton that can be selected using a mobile interface. When the button is pressed, the publication information is replaced by a short review of the book, and the "See Review" button is replaced with a "Hide review" button. When the "Hide Review" button is pressed, the back cover display returns to the original publication information.

A video demo of the code running can be found at https://youtube.com/shorts/cl3P3H3SdQI?feature=share. 

Limitations of this code largely relate to visual tracking of the target book covers. The program continues to track the book covers after they have moved out of frame. This can be problematic if there are other moving objects in the scene. Since the location of the book in 3D may be registed to other objects in the scene, the extended tracked position of the book cover may be inaccurate. Furthermore, in the presence of glare, dim lighting, or physical alterations to the book itself, the book cover may not be recognized.
The target image for the back cover was taken from a cropped photograph; therefore, the target image may have been subject to skew and glare, making it more difficult for the program to track (this can be seen in the demo video, where it takes much longer for the app to recognize the back cover. Finally, the program is based on the specific cover design for the 2004 Clarion Books edition and will not recognize alternative cover designs. 

To run this code, download the code as a zip file, and extract all files.

If not already installed, download and install the Unity Hub and Unitt editor version 2022.3.5. Launch Unity Hub. Under "Installs"->"2022.3.5f1", select settings icon->"Add modules" and verify that the Android Build Support platform with OpenJDK and Android SDK & NDK Tools have been installed. If these have not been installed, install them. In the Project window, open a new project in Unity with the 3D template using version 2022.3.5. Install and import the Vuforia Engine Package (if prompted, upgrade any dependencies). 

In the Unity project, Right click "Assets->Import New Asset...", navigate to the extracted file path, and select the display images: one-ring.png, smoke.png, sting.png, and strider.png.
If prompted, import TPM Essentials, Extras and Examples. 

Naviagate to the Assets folder in the Unity Project directory, and copy the BookCover.unity scene file to the project and open the scene in the Unity Editor.

Log into the Vuforia Developer Portal (or create a new account), and navigate to the Licenses page. If you do not have a liscence, select "Get Basic" to create a license. Select the licsencse, and copy the key to clipboard. In the Unity BookCover scene, select the ARCamera GameObject. In the properties window, select "Open Vuforia Engine configuration". After the configuration opens, paste the Vuforia license key in the field for "App License Key".

Return to the Vuforia Developer Portal, navigate to the target manager page. Select "Add Database->Device", and enter bookCovers for the database name. Upload the fellowship-back-cover.jpg and fellowship-of-the-ring-illustration-johan-egerkrans.jpg to the database, and enter 0.124 for the width for each cover image. Download the database, and open in the Unity project.

Return to the BookCover Unity scene. In the project hierarchy, expand "Front Cover Target->Canvas". For each of the respective images (One Ring, Strider, Smoke, Sting), select the object and in the inspector window, enter the corresponding .png image under "Raw Image->Texture".

When ready to run the project, connect a compatible Android device via USB. Make sure developer mode has been activated for the Android device.

Navigate to "File->Build Settings". Under "Platform", select "Android". Under "Android", select "Switch Platform". This will switch to the Android build settings. For "Run Device", select the Android device name. Click the box for "Development Build", then select "Build and Run". Enter a name for a new apk file for the build. Select "save" and allow the program to build to the Android device. Open the app, and image the book though the phone camera. To toggle between displays on the back cover, select "See Review" and "Hide Review" respectively.
