# Create Your Own AdMob Test Ads #

This guide shows you how to set up your own house ad campaign to test the ad flow in your applications.

  1. Log in to www.admob.com/my\_sites/ and click **Add Site/App**
  1. Fill out information to create a new site/app and click **Continue**. You can leave the **App Store URL** blank.
  1. Go to **Sites & Apps -> House Ads** and select **Create New House Ad Campaign** <br><img src='http://wiki.google-mobile-dev.googlecode.com/git/images/admob_add_site_app.png' />
<ol><li>Create a name for the campaign, and select the dates you want the house ads to run. Click <b>Save and Continue</b>.<br>
</li><li>Create a name for the ad group and select a house ad type you wish to serve.<br>
</li><li>Select the app to which you want to traffic the house ad campaign (your test app), and check the <b>Fully Allocate</b> box so that house ads always serve. Click <b>Continue</b>. <br><img src='http://wiki.google-mobile-dev.googlecode.com/git/images/admob_house_ad_group.png' />
</li><li>Leave the targeting options to all devices and locations, unless you intend to traffic house ads only under certain conditions. Click <b>Continue</b>.<br>
</li><li>Configure a text or image house ad. Click <b>Create Ad and Finish</b>.<br>
</li><li>Go back to the <b>Sites/Apps</b> page. Locate your newly created app and click <b>Manage Settings</b>. Find the publisher ID that’s trafficked to serve house ads. <br><img src='http://wiki.google-mobile-dev.googlecode.com/git/images/admob_publisher_id.png' />
</li><li>Use this publisher ID during development to test what happens when ads are clicked.</li></ol>

That’s it! You now have a fully functional test ad to use for development. Remember to swap out the test publisher ID for your live app’s publisher ID when you release. If you accidentally leave in the test publisher ID, you can remove the house ad campaign so that publisher ID starts serving live ads.<br>
<br>
<h1>Mediation</h1>

If you want to use house ads to backfill your unfilled mediation traffic, you'll need to take a couple additional steps.<br>
<br>
<ol><li>Find your mediation placement on mediation.admob.com, and select <b>Manage Settings</b>. Then click the <b>Add Ad Network</b> button.<br>
</li><li>Select <b>AdMob House Ads</b>, and scroll down to the bottom and configure this network to use your newly created publisher ID that always serves house ads. Select <b>Save</b> and then <b>Continue</b>.<br>
</li><li>Make sure the <b>AdMob House Ads</b> network is enabled, and give it an eCPM value to place it in the mediation flow.</li></ol>

You will now show house ads if AdMob mediation can't get an ad from other networks.