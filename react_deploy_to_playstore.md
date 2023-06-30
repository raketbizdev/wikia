# How to Deploy a React Native App to the Google Play Store Using Expo (2023 Edition)

## Prerequisites

Before we start, make sure you have the following:

- A Windows computer.
- Node.js and npm installed.
- An Android Studio for testing your app.
- A Google Play Developer account (note that a one-time $25 registration fee is required).
- Expo CLI installed. You can install it using npm by running the following command in your terminal:

```bash
npm install -g expo-cli
```

- An existing React Native app that you've built using Expo.

## Step 1: Set Up Your App's Configuration

The first step is to make sure your app's `app.json` file is properly set up. This file should be in the root of your project directory. Here's an example of what it might look like:

```json
{
  "expo": {
    "name": "Your App Name",
    "slug": "your-app-slug",
    "version": "1.0.0",
    "orientation": "portrait",
    "icon": "./path/to/your/app-icon.png",
    "splash": {
      "image": "./path/to/your/splash-image.png",
      "resizeMode": "contain",
      "backgroundColor": "#ffffff"
    },
    "updates": {
      "fallbackToCacheTimeout": 0
    },
    "assetBundlePatterns": ["**/*"],
    "ios": {
      "supportsTablet": true
    },
    "android": {
      "adaptiveIcon": {
        "foregroundImage": "./path/to/your/adaptive-icon.png",
        "backgroundColor": "#FFFFFF"
      }
    },
    "web": {
      "favicon": "./path/to/your/favicon.png"
    }
  }
}
```

Make sure to replace the fields with the specifics for your app. In particular, set a unique `slug` and specify your `icon`, `splash`, and `adaptiveIcon` images.

## Step 2: Build an Android APK or AAB

Next, you'll need to build an APK (Android Application Package) or AAB (Android App Bundle) of your app. This is the file that you will upload to the Google Play Store.

Building an APK (Android Application Package) or AAB (Android App Bundle) is the second step in the process. This involves compiling your React Native code into a file that can be uploaded to the Google Play Store and run on Android devices.

Here are the detailed steps:

1. Open your terminal. This could be Command Prompt, PowerShell, or a Terminal window, depending on your operating system.

2. Use the `cd` command to navigate to your project directory. For example, if your project is located in a folder named `MyApp` on your Desktop, you would type:

   ```bash
   cd Desktop/MyApp
   ```

3. Once you're in your project directory, you can tell Expo to start the build process with the following command:

   ```bash
   expo build:android
   ```

4. After you run this command, Expo will ask you whether you want to build an APK or an AAB. Here's what you need to know about these options:

   - **APK**: This is a traditional Android installation file. If you choose this option, your app will be built into a single APK file, which includes all the code and resources needed to run your app on any Android device. This file can be large, as it includes everything needed for every possible device configuration.

   - **AAB**: This is a newer format introduced by Google. If you choose this option, your app will be built into an Android App Bundle. When you upload this to the Google Play Store, Google will use it to generate optimized APKs for each device configuration that downloads your app. This means smaller download sizes for your users, as they only download the code and resources that their specific device needs. Google recommends using this option.

   To choose to build an AAB, simply type `aab` and press Enter.

5. Expo will then start the build process. This can take a few minutes. Once it's done, Expo will provide a URL where you can download your APK or AAB file.

Remember to keep this file safe, as you'll need it in the next steps!

Note: If your app uses any native code, you may need to eject from Expo and build your APK or AAB using Android Studio. However, if you're only using JavaScript and Expo's API, you can build your APK or AAB using the `expo build:android` command as described above.

## Step 3: Generate a Signing Key

When you run the build command for the first time, Expo will ask you whether you want it to handle the process of creating a signing key for you, or if you want to upload your own.

Since you don't have a signing key yet, choose 'Let Expo handle the process'.

Expo will then create the signing key and store it for you on their servers, which simplifies the process of building updates in the future.

## Step 4: Download Your AAB

After the build process is complete (it may take a few minutes), Expo will provide a URL where you can download your AAB. Download it and remember its location on your computer.

## Step 5: Create an App on Google Play Console

Go to the Google Play Console and sign in with your Google Play Developer account.

- Click on 'Create App'.
- Fill in your app's details, including its name, default language, and whether it's an```markdown
  app or a game.
- Choose the app category and select 'Free' or 'Paid'. Click 'Create App'.

## Step 6: Set Up Your App's Store Listing

Before you can publish your app, you need to fill out your app's store listing. This includes the following details:

- **Title**: The name of your app as it will appear on the Google Play store.
- **Short description**: A brief summary of your app.
- **Full description**: A detailed description of your app.
- **Screenshots**: Images showing off what your app looks like and what it does.
- **Hi-res icon**: A 512 x 512 32-bit PNG (with alpha).
- **Feature graphic**: A 1024 w x 500 h JPG or 24-bit PNG (no alpha).
- **Application type**: Whether your app is an application or a game.
- **Category**: The category that best fits your app.
- **Content rating**: You will fill out a questionnaire about your app's content so Google Play can provide an appropriate content rating.
- **Website, email, and privacy policy**: If you have a website and an email address, you can provide these. Google Play requires that you provide a privacy policy if you wish to request sensitive permissions or handle sensitive user data.

Fill out all of these details and then save your changes.

## Step 7: Set Up Your App's Content Rating

Google Play requires that you provide a content rating for your app. To do this, you will fill out a questionnaire about your app's content. Once you've completed the questionnaire, Google Play will assign a content rating to your app.

## Step 8: Set Up Your App's Pricing and Distribution

In the Pricing & Distribution section, you can choose whether your app will be free or paid, and which countries it will be distributed in. Fill out this information and then save your changes.

## Step 9: Enable Google Play App Signing

Google has introduced a new app signing method that allows the key store file to be preserved on the Play Store. This relieves the developer from storing the key store file locally and keeping it safe.

To enable Google Play App Signing, follow these steps:

1. In the Google Play Console, select your app.
2. On the left menu, select 'Release management' > 'App releases'.
3. Next to 'App signing by Google Play', select 'Accept' option.
4. On the left menu, select 'App Signing' option. You can see the 'App signing certificate' and 'Upload certificate' options.
5. Make sure you download the 'App Signing Certificate' too. The main benefit of the Android App Bundle is that Google will re-sign the APK with the deployment key, and will generate APKs as per device configuration.

## Step 10: Upload Your App's AAB to Google Play Console

Now, you're ready to upload your app's AAB to the Google Play Console. Go to the 'Release management' page, then 'App releases', and then click on 'Create Release'. Here, you can upload your AAB file.

After you've uploaded your AAB, you'll have a chance to review all of your app's information before it goes live. Once everything is correct, click 'Review', then 'Start Rollout to Production'. Your app will then be reviewed by Google and, if approved, will be published on the Google Play Store.

Congratulations, you've deployed a React Native App to the Google Play Store using Expo!

## Things to Look Out For

- Ensure that all details in the Google Play Console are filled accurately, as these will be visible to the users on your app's listing.
- Keep your app updated regularly to meet user demands and fix any bugs.
- Monitor user feedback and ratings to understand user needs and improve your app accordingly.
- Always test your app thoroughly before deploying to catch and fix any bugs.
- Follow all Google Play policies to avoid having your app suspended or removed from the Play Store.
- Keep your signing key safe. If you lose access to it, you won't be able to update your app.

With these steps, you should be able to successfully deploy your React Native app to the Google Play Store using Expo. Happy coding!

## Most common Mistakes

1. **Losing the Key Store File:** It was previously your responsibility to keep the key store safe for future updates. If you lost it, you had to create a new application and lose all previous reviews and ratings. To overcome this, Google introduced a new App signing method that preserves the key store file on the Play Store, relieving the developer from storing the key store file locally​1​.

2. **Incorrectly Enabling Google App Signing:** When preparing your release in Google Play Console, you need to enable Google App Signing correctly. For new applications, you need to accept the App signing by Google Play. For existing applications, you need to upload a key exported from Android Studio. It's important to download the App Signing Certificate as well. If done incorrectly, this can result in issues such as Google Maps not loading in the Android app in release mode​1​.

3. **Incorrect Screenshot Dimensions:** When uploading screenshots to the Google Play Store, the image has to have a minimum length of 320px for any side, and a maximum length of 3840px for any side. If this is not done properly, you may face issues while uploading the screenshots. The solution is to ensure the screenshots are of the correct dimensions​​.

## Additional Resources

For visual guides, here are some YouTube videos that can help you:

[![How to Build, Test, and Deploy Your React Native Expo App to the Google Play Store](https://img.youtube.com/vi/pb6OvvSi8Qk/sddefault.jpg)](https://www.youtube.com/watch?v=pb6OvvSi8Qk)

This tutorial should help you deploy your React Native app to the Google Play Store. If you encounter any issues, feel free to ask for help.
