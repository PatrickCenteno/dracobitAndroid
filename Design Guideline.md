##Design Overview  

####The purpose of this document is to layout out the basic architecture that this app will follow  

###Patrick Centeno  

Here is the goals for the authetication and connecting to the api

### App validation workflow

An activity is a like a web page if you dont already know
I will be making reference to activity lifecycle methods the refer when the activity is loaded or destroyed
(onCreate(), onStart(), onStop(), onRestart())
In addition to normal user table in DB, we will have a mobile user table with informaiton about them relative to the app: 1. logged in status 2. changed password status 3. What devices they are or have logged in from

Public API key for the app: // file with key cannot go in repository key will change with each version of the app

onCreate() of initial splashscreen: Check API key Check API key with every call and tie different API keys to different versions of app

After initial check, check if user was registered with device // if theyve logged in before

if they are, hit mobile user table to find out if they are logged in or they changed the password

if they are not logged in or password was changed, hit login activity

if no user on device, hit sign up activity // can easily go to login activity from there // This can be implemented by having one login/signup activity with two different fragments for each one

if logged in, retreive a userkey from mobile user table

User key is passed with every API call (relative to user specific info) from here onward API key is also passed to determine app version and authenticate destination of request

onStop(): save user id in Shared prefernces or sqlite db // built in android db

onRestart(): retreive user id if no user id exists - that means they logged out and attempt to retreive user id from mobile user table again

onStart(): // of every activity except splashscreen retrieve request token

Its important to note that we can keep track of the device name that the user is logged into on the backend
