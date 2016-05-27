# Project Goals / Objectives 

Here you can list any technologies you'd like to work with, learn or improve upon.
You can add any technologies you'd like to work with and learn below.

### Mohammed Amin ~
As this is a learning experience, 
some of the technologies that I'd like to learn/incorporate into this project 
and that I feel would be very useful in the long run are the following:  

[Dagger 2](http://google.github.io/dagger/)  
[Retrofit 2](http://square.github.io/retrofit/) OR [Volley](https://android.googlesource.com/platform/frameworks/volley)  
[RxJava/RxAndroid](https://github.com/ReactiveX/RxAndroid)  
[Realm](https://realm.io/) / [Firebase?](https://firebase.google.com/)  
#### Testing
UI Testing: [Espresso](https://google.github.io/android-testing-support-library/docs/espresso/)  
Unit Testing: [Robolectric](http://robolectric.org/) | [JUnit4 / Mockito](https://developer.android.com/training/testing/unit-testing/local-unit-tests.html)  

### Patrick Centeno
Here is the goals for the authetication and connecting to the api

 ### App validation workflow
 * An activity is a like a web page if you dont already know
 * I will be making reference to activity lifecycle methods the refer when the activity is loaded or destroyed 
 * (onCreate(), onStart(), onStop(), onRestart())

In addition to normal user table in DB, we will have a mobile user table with informaiton 
about them relative to the app:
	1. logged in status
	2. changed password status
	3. What devices they are or have logged in from



Public API key for the app: // file with key cannot go in repository
key will change with each version of the app 

onCreate() of initial splashscreen:
	retreive request token with public API key
	we can tie request tokens to different versions of the app restrict certain services
	Passes this request token with every call


After token is received, check if user was registered with device // if theyve logged in before

if they are, hit mobile user table to find out if they are logged in or they changed the password

if they are not logged in or password was changed, hit login activity

if no user on device, hit sign up activity // can easily go to login activity from there
	// This can be implemented by having one login/signup activity with two different fragments for each one

if logged in, retreive a userId token from mobile user table (or regular user table)

User id token is passed with every API call (relative to user specific info) from here onward


onStop():
	save user id in Shared prefernces or sqlite db // built in android db

onRestart(): 
	retreive user id
	if no user id exists - that means they logged out and attempt to retreive user id from mobile user table again


onStart(): // of every activity except splashscreen
	retrieve request token

  
