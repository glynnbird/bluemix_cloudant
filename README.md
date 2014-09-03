## bluemixcloudant - Node.js library for Cloudant running on IBM BlueMix

This project simply loads an instance of Nano (the Node.js CouchDB library) and configures it with your 
Cloudant parameters when running in IBM's BlueMix environment.

* if you are running locally, Nano is configured with local CouchDB
* if you are running in BlueMix, Nano is configured with the first Cloudant service it comes across in BlueMix's environment variables

### Using bluemixcloudant

Add "bluemixcloudant" in your package.json's dependencies object:

```
dependencies: {
  "bluemixcloudant": ""
}
```
and run

```
npm install
```

You can then use bluemixcloudant in your code:
```
var cloudant = require('bluemixcloudant');
cloudant.get('rabbit', { revs_info: true }, function(err, body) {
  if (!err)
    console.log(body);
});
```
The returned "cloudant" object is actually a Nano instance, preconfigured with either local CouchDb or BlueMix's Cloudant service, gleaned from the environment.
