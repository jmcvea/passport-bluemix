## passport-ibm



## Usage

var passport = require('passport')
  , OAuth2Strategy = require('passport-oauth').BlueMixOAuth2Strategy;

passport.use('provider', new BlueMixOAuth2Strategy({
    authorizationURL: 'https://www.provider.com/oauth2/authorize',
    tokenURL: 'https://www.provider.com/oauth2/token',
    clientID: '123-456-789',
    clientSecret: 'shhh-its-a-secret'
    callbackURL: 'https://www.example.com/auth/provider/callback',
    requestedAuthnPolicy: 'http://www.ibm.com/idaas/authnpolicy/basic'
  },
  function(accessToken, refreshToken, profile, done) {
    User.findOrCreate(..., function(err, user) {
      done(err, user);
    });
  }
));


Protect your Routes:
app.get('/auth/provider', passport.authenticate('provider'));

// The OAuth 2.0 provider has redirected the user back to the application.
// Finish the authentication process by attempting to obtain an access
// token.  If authorization was granted, the user will be logged in.
// Otherwise, authentication has failed.
app.get('/auth/provider/callback', 
  passport.authenticate('provider', { successRedirect: '/',
                                      failureRedirect: '/login' }));
                                      
Specify your scope: (default = profile)


## Developing


## Test (to come)




