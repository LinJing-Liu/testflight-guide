# Guide for Preparing App for Upload to TestFlight via XCode
*Note: This guide only outlines steps for preparing the app for upload to TestFlight, assuming that steps to setup the provisioning files and AppleDeveloper account has been completed already.*

## Prepare Project Settings
- With workspace file of the app opened, go to xcodeproj of the app (same name as the app folder) and select on the target for which the upload to TestFlight will be done for. The targets are iOS, tvOS and macOS.
- Select `Signing & Capabilities` and deselect `Automatically manage signing`. Import the appropriate provisioning file for the app and select the team if necessary.

  Edit the `Bundle Identifier` to align with the name originally used to setup the provisioning files.
  XCode will indicate the correct bundle identifier if you don't remember the exact one.

![Signing Settings](https://github.com/LinJing-Liu/testflight-guide/blob/main/pictures/signing_and_capabilities.png)

## Add AppIcons
- Open `Assets` and then `AppIcon`. An *App Store iOS* icon of **1024px** is required. Additional app icons will also be needed depending on whether the app is built for iPhone, iPad or Mac.
  - Images for the icons can be dragged directly into `Assets` to add them.
  - Make sure the icons meet the size requirements.
  - The icons also have to be opaque with no transparency.
  - It is possible that the icons may appear to be not transparent yet not pass the validation phase, refer to this [StackOverflow post](https://stackoverflow.com/questions/25681869/images-cant-contain-alpha-channels-or-transparencies)
for how to use preview to remove transparent background.

## Optional: Add Launch Screen
- Add a custom launch screen to the app if desired. Use the `LaunchScreen Storyboard` under the specific target to modify the design of the launch screen.

## Create an Archive of the App
- Before creating an archive, make sure that a generic device (ex: Any iOS Device) is selected for build so that the archive will be created for a general device and not include files specific to a real device or simulator.
- Then go to `Product > Archive` to produce an archive for the app.
  This process can potentially take 45 to 60 mins depending on the pod used in the project and project dependencies.
 
 ![Archive Selection](https://github.com/LinJing-Liu/testflight-guide/blob/main/pictures/archive_selection.png)
 ![Selection to View Archives](https://github.com/LinJing-Liu/testflight-guide/blob/main/pictures/organizer_selection.png)
 
 ![Archives](https://github.com/LinJing-Liu/testflight-guide/blob/main/pictures/archive_view.png)
 
 ## Complete Distribution of the App 
- When the archive is completed, a new window will show up with the archive. This view can also be brought up using `Window > Organizer`.
- Make sure the most recent archive is selected and use `Validate App` to first check whether the archive can be uploaded to TestFlight and resolve any issues as necessary.
  After resolving issues, a new archive will need to be generated.
- After passing the validation, select `Distribute App` and `App Store Connect` for distribution method. Add the provisioning file and fill options related to the app when they emerge. A success message will be displayed if the distribution is completed.

!(Distributing in Progress)[https://github.com/LinJing-Liu/testflight-guide/blob/main/pictures/uploading_in_progress.png]

## Resources
The following resources outline steps for uploading to TestFlight in greater detail.
- [Distributing Your App for Beta Testing and Releases (App Developer)](https://developer.apple.com/documentation/xcode/distributing-your-app-for-beta-testing-and-releases)
- [Distribute an app using TestFlight (iOS, tvOS, watchOS)](https://help.apple.com/xcode/mac/current/#/dev2539d985f)
