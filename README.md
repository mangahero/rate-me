Rate-Me
=======

Rate-Me is a Librery for Android2.3+ that provides a Dialog for suggesting to the user a Rate the App. If the Rate is 4 or more stars, the Dialog goes to PlayStore
You can see the [source code](https://github.com/androidsx/rate-me/blob/change-Readme/LibraryRateMe/src/com/androidsx/rateme/DialogRateMe.java) and an application example 

If the rating is 4 or more stars, the dialog just takes the user to the Google Play store. Otherwise, it prompts them to give feedback to the developer.
You can see the [main class here](https://github.com/androidsx/rate-me/blob/change-Readme/LibraryRateMe/src/com/androidsx/rateme/DialogRateMe.java) and an integration example in this image:
[![img1](https://raw.githubusercontent.com/androidsx/rate-me/master/images-readme/image.png)]()

## How to use

Using the library is really simple, [that example](https://github.com/androidsx/rate-me/blob/change-Readme/RateMe/src/com/androidsx/rateme/demo2/HelloWorldActivity.java)  allows you to know how to link the activity apps through a button.
When you want to use this Library you need three constant in you proyect:

				private static final String EMAIL = "yourmail@mail.com";
			    private static final int INSTALL_DAYS = 20;
			    private static final int LAUNCH_TIMES = 5;

you can add another constant:

				private static final String MY_PACKAGE_NAME = "com.androidsx.smileys";
				
On the button click event, you have add this code.

			DialogFragment dialogo = DialogRateMe.newInstance(
				            MY_PACKAGE_NAME,EMAIL);
			        dialogo.show(getFragmentManager(), "dialog");
     
normally use `getPackageName()` instead of `"com.androidsx.smileys".`

This Library can be opened automatically by calling the method onStart in our project and pass the constant ´INSTALL_DAYS´ and ´LAUNCH_TIMES´:

			@Override
			    protected void onStart() {
			        super.onStart();
			        RateMeDialogTimer rateDialog = new RateMeDialogTimer(INSTALL_DAYS,LAUNCH_TIMES);
			        RateMeDialogTimer.onStart(this);
			        if (RateMeDialogTimer.shouldShowRateDialog(this)) {
			            DialogFragment dialogo = DialogRateMe.newInstance(
			                    MY_PACKAGE_NAME,EMAIL);
			            dialogo.show(getFragmentManager(), "dialog");
			        }
        
			    }			

###CustomCriteria

The default criteria to show the dialog is as below:

* App is launched more than 20 days later than installation.
* App is launched more than 10 times

you can change this settings [here](https://github.com/androidsx/rate-me/blob/change-Readme/RateMe/src/com/androidsx/rateme/demo2/HelloWorldActivity.java) in the variable `INSTALL_DAYS` and `LAUNCH_TIMES`
