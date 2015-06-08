### Version 3.1 - July 26, 2010 ###
  * Bug fixed: Allow DoubleClick publishers to set a custom GoogleAdView size.
  * Bug fixed: Add `onAdFetchFailure()` to AdViewClient, which catches cases where DoubleClick cannot fill the request.
  * Enable plugins in GoogleAdView so that Flash ads will be able to display.

### Version 1.7 - May 20, 2010 ###
  * Bug fixed: Expanded ad consumes back key instead of dismissing.
  * Bug fixed: Spinner dismissed and `onFinishFetchAd` called prematurely.


### March 31, 2010 ###
  * Expandable ads are supported. To enable, set the direction of ad expansion.
  * Note: Be sure to set the background color for alternate ad URLs because the default is now transparent. Also ensure that your alternate ad URL does not have redirects. This will be supported in a future release.

### February 2, 2010 ###
  * `showAds()` should not request for ads when Activity is in the background.

### December 17, 2009 ###
  * 300x250 text and image Google ads are supported. Please refer to the policy guidelines governing use of this ad unit.
  * Automatic refreshing of Google ads is supported. The minimal time between refreshes is 3 minutes.
  * DoubleClick example is fixed.

### November 24, 2009 ###
  * User language setting on device is taken into account when serving ads.

### November 3, 2009 ###
  * Bug fixed: Ads on QVGA devices are displaced/cutoff and ads on WVGA devices require scrolling.
  * Bug fixed: Fixed runtime incompatibility with Cupcake.