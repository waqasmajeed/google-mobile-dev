### Version 3.1 - August 2010 ###
  * Removed requirement to have kGADAdSenseClientID in AdSense requests. If one is not supplied, the built-in value will be used. If you do specify a value for this field, it must match the built-in value or a `GAD_UNEXPECTED_PUBLISHER_ID` error will be returned.
  * Removed option to `GAD_ACTION_LAUNCH_SAFARI` for AdSense as keeping the user in the application results in a better experience. Since the "Open in Safari" button is available in the internal website view, it is still possible for a user to open pages in Mobile Safari.
  * Added `GAD_ACTION_DISPLAY_NONE` option to DoubleClick requests only. This option will register the click with Google Servers, but will not open any web pages.
  * Added support for iPad ad format (728 x 90).
  * Updated examples to work on iPad.
  * Bug Fix: Remove duplicate object file definitions in library.
    * http://code.google.com/p/google-mobile-dev/issues/detail?id=13
  * Bug Fix: Checking for network connectivity is now asynchronous.
    * http://code.google.com/p/google-mobile-dev/issues/detail?id=8
  * Bug Fix: Creating a second instance of GoogleAdView no longer causes a slowdown in accelerometer performance.
    * http://code.google.com/p/google-mobile-dev/issues/detail?id=11

### Version 3.0 - June 21, 2010 ###
  * Added support for iOS 3.2 and 4.0
  * Single binary SDK for i386, armv6, and armv7

### May 20, 2010 ###
  * Requirement: You must set the `kGADAdSenseApplicationAppleID` for AdSense requests. See the header file for more information.
  * Feature: Non-black and white gradients are supported.  Set the `kGADAdSenseAdTopBackgroundColor` to customize your gradient background color.
  * Feature: Non-family safe ads are supported. Set `kGADAdSenseAllowAdsafeMedium` to get both family safe and non-family safe Google ads.
  * Feature: Double-Click publishers can specify AdSense keywords parameter for backfill by setting the `kGADDoubleClickAdSenseKeyword`.
  * Bug Fixes

### April 8, 2010 ###
  * Added support to 3.0 GoogleAdsSDK for iPhone OS 3.2 compatibility.
  * Also including 3.2 GoogleAdsSDK with beta support for building native OS 3.2 iPad applications.

### March 31, 2010 ###
  * We're providing a single binary (the OS 3.0 version) that should work with iPhone OS 3.0 through OS 3.1.3. We are deprecating support for OS 2.x.
  * Expandable ads are supported. To enable, set the direction of ad expansion.
  * `loadSucceeded` and `loadFailed` are supported for non-audio AdSense requests.
  * Note: Be sure to set the background color for alternate ad URLs because the default is now transparent. Also ensure that your alternate ad URL does not have redirects. This will be supported in a future release.

### February 2, 2010 ###
  * We're providing a single binary (the OS 3.x version) that should work with both OS 2.x and 3.x applications. We're also including the OS 2.x version to be used if your application doesn't support OS 3.x.
  * Added support for advertiser's website view to be displayed in landscape orientation. On OS 2.x devices, the SDK will respect the supported orientations of the main view controller.

### December 17, 2009 ###
  * 300x250 text, image, and audio Google ads are supported. Please refer to the policy guidelines governing use of this ad unit. Only the ad text is clickable; there are known issues with clicking on the blank space around the ad text.
  * Google ads are not served when the device is locked.
  * When ads displayed in portrait mode are rotated to landscape mode, the same ad will be displayed. The advertiser's webpage for now will still be in portrait mode.

### November 24, 2009 ###
  * The user language setting on the mobile device is taken into account when serving Google ads.
  * The delegateWebsiteView has a "Done" button for the user to immediately return to the application content where a Google ad was shown.
  * `adControllerDidCloseWebsiteView` indicates when the advertiser's website controller has been closed.
  * `autoRefreshSeconds` allows for automatic refreshing of Google ads. The minimal time between refreshes is 3 minutes.
  * Advertiser-specified frequency capping is supported.

### September 9, 2009 ###
  * Online AdSense audio ads is another ad format that Google serves.
  * The channel ID in the AdSenseExample is fixed to be of type string instead of long.