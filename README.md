# twitter-connect-plugin
Cordova/PhoneGap plugin to use Twitter Single Sign On

### Install

##### Create a Twitter app
Create a Twitter application and get the consumer key and consumer secret.

##### Add plugin to your Cordova app
`cordova plugin add twitter-connect-plugin --variable FABRIC_KEY=<Fabric API Key>`

Make sure you put in your valid Fabric API Key in place of `<Fabric API Key>`.

##### Add configuration to config.xml
Open `config.xml` (in your project's root) and add these two lines before the closing ```</widget>``` tag:
````
<preference name="TwitterConsumerKey" value="<Twitter Consumer Key>" />
<preference name="TwitterConsumerSecret" value="<Twitter Consumer Secret>" />
````
Of course, replace the values with the keys you got from the above steps.

For iOS, the deployment target needs to be at least 7.0. You can set this in the config.xml file like so:
````
<preference name="deployment-target" value="7.0" />
````

##### Finished!
You should now be able to: `cordova run android` or `cordova run ios`

### Phonegap Build
Add the following to your config:

```
<gap:plugin name="twitter-connect-plugin" source="npm" spec="0.5.0">
	<param name="FABRIC_KEY" value="<Fabric API Key>" />
</gap:plugin>
```

You'll need to specify iOS7 for TwitterKit
```
<preference name="deployment-target" value="7.0" />
```

### Usage

This plugin adds an object to the window named TwitterConnect. Right now, you can only login and logout.

##### Login

Login using the `.login` method:
```
TwitterConnect.login(
  function(result) {
    console.log('Successful login!');
    console.log(result);
  }, function(error) {
    console.log('Error logging in');
    console.log(error);
  }
);
```

The login reponse object is defined as:
```
{
  userName: '<Twitter User Name>',
  userId: '<Twitter User Id>',
  secret: '<Twitter Oauth Secret>',
  token: '<Twitter Oauth Token>'
}
```

##### Logout

Logout using the `.logout` method:
```
TwitterConnect.logout(
  function() {
	console.log('Successful logout!');
  },
  function() {
    console.log('Error logging out');
  }
);
```
