<p align="center">
<img src="https://firebase.google.com/downloads/brand-guidelines/SVG/logo-standard.svg" height="60"/><br/>
</p>


# Advantages of Firebase
 - Cloud storage/database options
 - Easy integration with Android Studio
 - Easy to understand
 - Language support (sometimes provided through wrappers)
 
> At this point, you're probably wondering when I'm going to cut to the chase. And don't worry, the tutorial is below, but understand that this tutorial is barely the tip of the iceberg - for real answers, please check out the Firebase documentation.

1. Go to the Tools > Firebase menu option and click on it.
![Start](https://i.ibb.co/Ph5sMtG/image.png)
2. You should see a few listings pop up in a menu on the side (including "Analytics," "Cloud Messaging," and "Authentication"). For the purpose of this tutorial, we're going to be checking out the database feature (entitled "Realtime Database"). After expanding this option, you'll see a link labeled "Save and Retrieve Data." Proceed to click the link.<br/>
![Save and Retrieve Data](https://i.ibb.co/2Ymk1cb/image.png)
3. Now, you should see a button entitled "Connect to Firebase". Click this button and log in to your Google Account (presumably not your school account) after clicking the "Sign In" button located in the top right section of our dialog box. Firebase will ask you to provide them a few permissions. Allow it to access all of these permissions.
![Permissions](https://i.ibb.co/fFX2pFQ/image.png)
4. Now go back to Android Studio and click the blue button labeled "Connect to Firebase." The gradle will now add the settings that will allow you to connect to the database. Once the gradle is done, a message will appear in the bottom right corner of Android Studio saying "Firebase project created." If everything worked, you should see a checkmark as shown below:<br/>
![Check](https://i.ibb.co/wMyCYst/image.png)<br/>


5. If all is well, proceed to click the "Add the Realtime Database to your app" button. You'll see a dialog come up. Click "Accept Changes."
![Accept Changes](https://i.ibb.co/sj257RJ/image.png)

6. After roughly one minute, the gradle will build the dependencies into your project. Once the gradle is finished, you'll see a checkmark next to the Android Studio icon in your taskbar.

7. The database is now connected. From here, you should set up your database rules. Now go to the ![Firebase Console](https://console.firebase.google.com/) (**Note:** make sure you're using the Google Account that you used to register for Firebase). You should see a block with your project name (mine is "Lender," in the image below)<br/>
![Project Console](https://i.ibb.co/M2HLRSs/image.png)

8. Once you go to your project in the Firebase console, expand the "Develop" tab on the left side of the console. There, you should see a menu option entitled "Database" - click it.<br/>
This is where you should be: ![Location](https://i.ibb.co/tKnHHSd/image.png)

9. Scroll down until you see this:
![Realtime DB](https://i.ibb.co/7Yn2RSt/image.png)
Click "Create Database."

10. **Make sure you select the option "Start in test mode."** The reason for this is that we don't want to have to go through the process of authentication (at least, not yet). If you're tired of this tutorial, just imagine how much worse it would be if we set up an Auth system. Anyways, your settings should appear as follows:<br/>
![Settings](https://i.ibb.co/b1MR0nr/image.png)



11. If you didn't heed my advice (in bold, by the way), click the "Rules" tab. Your rules should be set to:
`
{
  "rules": {
    ".read": true,
    ".write": true
  }
}
`
**Make sure to click "Publish changes." Also make sure you read my BOLD message this time :)**
![Rules smh](https://i.ibb.co/cgCYjTY/image.png)

11. Navigate back to the data tab:
![Now](https://i.ibb.co/Nt2Q2zY/image.png)
This is where you'll view all of the data changes triggered by the app (but not yet, of course).

12. The database is now fully set up. Now go back to `MainActivity.java` in Android Studio and add the following code:
```java
        // If you're having trouble accessing the classes below, add this import statement: import com.google.firebase.database.*;
        FirebaseDatabase database = FirebaseDatabase.getInstance(); // Database Instance
        DatabaseReference myRef = database.getReference("message"); // A folder named "message." This will be created automatically if it doesn't exist
        myRef.setValue("Mr. Mauro's class is awesome!"); // Now this, right here, is just a fact.
```

14. Run your app. A new data entry should have been created in your database (which should be viewable in the Firebase Realtime Database Console) saying "Mr. Mauro's class is awesome!" If not, go back to Step 1. Just kidding. Post a question on this repository, and then I can help you out. Mr. Mauro should be able to help, too, since he's cool 😎 `Right, Mr. Mauro?`.
