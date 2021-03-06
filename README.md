# Creating a MEAN stack app, the aim being to act as a Film & TV social media site.

#### README file 1.8.8

DEMO:

- Now live [here](https://shrouded-coast-27950.herokuapp.com/), still ironing out bugs that aren't present in local deployment
- From root of project, run node/nodemon server.js
- At this moment, for the full effect it's recommended to: 

> - Pull this repo and run locally for full effect.

> - Register then use a quick social login for full interaction capabilities.

Core Functionality:

- IM chat feature
- Read/write/like articles from News Feed
- Read/write/like comment&threads from Forum
- Learn about actors, actresses etc.

Requirements:

- NodeJs and MongoDb are required to be installed locally

---

Added in previous commits (1.1)

- Have added registration capabilites inc. relevant error checking and handling.
- Incorporated a factory to handle registration calls
- Make use of $location and $timeout services
- Small amount of message styling using ngAnimate

Added in previous commits (1.2)

- Basic Login functionality, referencing our local db only.

Added in previous commits (1.3)

- Use of JSON web tokens (jwt) to set and get user cookies
* Additional functions in authServices.js to handle set/get of cookie
- New factories: AuthToken and AuthInterceptors, the latter being used in conjunction with $httpProvider in our app.js file to ensure all http requests are intercepted and sent to this factory to determine whether a cookie exists, and to attach tot he header if so.
- Referencing $rootScope to ensure code to verify if user is logged in is executed each time the route/view changes.
- Conditional loading of our body(set from mainCtrl.js) to ensure unwanted nav elements aren't temporarily in view when running a slow connection(eg - preventing the display of login when user is logged in.) Also ngCloak to ensure no flickering of elements upon load.
- Logout view for demo
* view and route added to routes.js
- Profile view for demo
* view and route added to routes.js

Added in previous commits (1.4)

- Added Facebook login token using passport.js(de-/serialized user info). Includes redirecting of window to ensure no additional tabs are opened. Our routes file also redirects any errors back toward login screen. Carried out with OAuth 2.
- Another call to AuthToken factory for a token, similar to local login, this time venturing out toward facebook for a token then verifying user's existence within our own db.

Added in previous commits (1.5)
- Twitter(OAuth 1) and Google+(OAuth 2) login functionality.

Added in previous commits (1.6)
- Prevention of register, login and then the profile views depending on sign-in status.

Added in previous commits (1.7)
- Backend validation through Mongoose and use of Regex

Added in previous commits (1.7.2)
- Frontend form validation(displaying non-null requirement message, as well as specific requirements of each field)
- Adding additional layer of validation to our userCtrl
	* When a form is submitted, normally navigate to userCtrl and call "User.create" function, which itself will call our userServices factory(passing the form data along with it), with the factory then calling a http post in api.js. Back in userCtrl, "User.create" has a callback so we can inform the user of success and perform our usual redirect.
	* With these new changes, we're now checking if the form is valid before we leave our userCtrl, thus adding further frontend validation, as we don't have to wait until reaching the backend post action in order to find out whether there was an null error or not.
	* Note: Username takes underscores, but not hyphens.

Added in previous commits (1.7.3) (an add-on to backend validation)
- Custom directives, initially for use with a confirm password field.
- Check DB for username and email from client onblur(lostfocus).
- Prettify inputs by using load animation onblur, need to throttle connection for full effect.

Added in previous commits (1.8) 
- Rewrote backend to model 1:M relationships whereby an Object represents "1", and a nested array property represents the "Many". Data was previously modelled around link tables to represent a 1:M.

Added in previous commits (1.8.1-4) 
- Misc UI work.

Added in previous commits (1.8.5) 
- Deployed to Heroku

Added in previous commits (1.8.6) 
Abandoned 2-tier responsive navbar in favour of mobile friendly(hamburger on resize) design

Added in previous commits (1.8.7) 
- Registration form validation can now take .co.uk, .com.au(and similar) email addresses

---

Since last commit:

- Fixing feed issue whereby user sometimes had issues with display of articles when logged-in

> - Had to stop setting token in my header when talking to external IP
