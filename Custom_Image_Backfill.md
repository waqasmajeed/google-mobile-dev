# Introduction #

There are times when an ad request can’t be filled--for example, when the internet connection goes out on a mobile device.  This page contains the complete code for an example on how to show a custom image when AdMob fails to return an ad. Please refer to the blog post series ([part 1](http://googleadsdeveloper.blogspot.com/2012/06/show-custom-image-when-no-admob-ad-is.html) | [part 2](http://googleadsdeveloper.blogspot.com/2012/06/show-custom-image-when-no-admob-ad-is_21.html)) for a walkthrough of the code.


# Android #

**main.xml**

```
<?xml version="1.0" encoding="utf-8"?>
<LinearLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="fill_parent"
    android:layout_height="fill_parent"
    android:orientation="vertical" >
    <LinearLayout android:id="@+id/adLayout"
        android:layout_width="fill_parent"
        android:layout_height="wrap_content">
        <ImageView android:id="@+id/image"
            android:layout_width="wrap_content"
            android:layout_height="wrap_content"
            android:src="@drawable/testimage"
            android:visibility="gone" />
    </LinearLayout>
</LinearLayout>
```

**NoInternetActivity.java**
package com.example;

import android.app.Activity;
import android.content.Intent;
import android.net.Uri;
import android.os.Bundle;
import android.os.Handler;
import android.view.View;
import android.view.View.OnClickListener;
import android.widget.ImageView;
import android.widget.LinearLayout;

import com.google.ads.Ad;
import com.google.ads.AdListener;
import com.google.ads.AdRequest;
import com.google.ads.AdRequest.ErrorCode;
import com.google.ads.AdSize;
import com.google.ads.AdView;

public class NointernetActivity extends Activity implements AdListener, OnClickListener {
  private final static int REFRESH_RATE_IN_SECONDS = 60;
  private final Handler refreshHandler = new Handler();
  private final Runnable refreshRunnable = new RefreshRunnable();
  private boolean firstAdReceived = false;
  private AdView adView;
  private ImageView imageView;

  /** Called when the activity is first created. */
  @Override
  public void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.main);

    // Create an AdView and add it to the layout. Calling loadAd() is not
    // necessary in this case because onStart() will be called shortly
    // afterwards, which kicks off a Runnable that loads an ad into the AdView.
    adView = new AdView(this, AdSize.BANNER, "YOUR_AD_UNIT_ID");
    adView.setAdListener(this);
    LinearLayout layout = (LinearLayout) findViewById(R.id.adLayout);
    layout.addView(adView);
    imageView = (ImageView) findViewById(R.id.image);
    imageView.setOnClickListener(this);
  }

  @Override
  public void onClick(View view) {
    // Open a web browser and take the user to http://www.google.com.
    Intent intent = new Intent(Intent.ACTION_VIEW, Uri.parse("http://www.google.com"));
    startActivity(intent);
  }

  @Override
  public void onStop() {
    super.onStop();
    // Remove any pending ad refreshes.
    refreshHandler.removeCallbacks(refreshRunnable);
  }

  @Override
  public void onStart() {
    super.onStart();
    if (!firstAdReceived) {
      // Request a new ad immediately.
      refreshHandler.post(refreshRunnable);
    }
  }

  @Override
  public void onReceiveAd(Ad ad) {
    firstAdReceived = true;
    // Hide the custom image and show the adView.
    imageView.setVisibility(View.GONE);
    adView.setVisibility(View.VISIBLE);
  }

  @Override
  public void onFailedToReceiveAd(Ad ad, ErrorCode code) {
    if (!firstAdReceived) {
      // Hide the AdView and show the custom image.
      adView.setVisibility(View.GONE);
      imageView.setVisibility(View.VISIBLE);

      // Turn off the click listener if there is a network error.
      if (code == ErrorCode.NETWORK_ERROR) {
        imageView.setOnClickListener(null);
      } else {
        imageView.setOnClickListener(this);
      }

      // Schedule an ad refresh.
      refreshHandler.removeCallbacks(refreshRunnable);
      refreshHandler.postDelayed(refreshRunnable, REFRESH_RATE_IN_SECONDS * 1000);
    }
  }

  @Override
  public void onPresentScreen(Ad ad) {
  }

  @Override
  public void onDismissScreen(Ad ad) {
  }

  @Override
  public void onLeaveApplication(Ad ad) {
  }

  private class RefreshRunnable implements Runnable {
    @Override
    public void run() {
      // Load an ad with an ad request.
      adView.loadAd(new AdRequest());
    }
  }
}```