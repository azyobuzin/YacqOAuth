# YacqOAuth #
[OAuth 1.0](http://oauth.net/core/1.0a/) Client Implemented in [YACQ](http://www.yacq.net/)

## Example ##
	(load "YacqOAuth")
	(load "cts:System.Net")
	
	"https://api.twitter.com/1/statuses/home_timeline.json"
	.(let uri
		(createAuthorizationHeader
			"GET"
			Uri.(new uri)
			""
			"consumer key"
			"consumer secret"
			"access token"
			"access token secret"
			HMAC-SHA1
			""
			""
			Dictionary.[String String].(new)
		).(let oauthHeader
			WebClient.(new).(use wc
				wc.Headers.(Add "Authorization" oauthHeader)
				wc.(DownloadString uri).(print)
			)
		)
	)

## Symbols ##
### createAuthorizationHeader ###
Create "Authorize" header.

#### Arguments ####
- httpMethod : String
- uri : Uri
- realm : String
- consumerKey : String
- consumerSecret : String
- token : String
- tokenSecret : String
- signatureMethod : String
- callback : String
- verifier : String
- params : IEnumerable.[KeyValuePair.[String String]]

#### Return ####
String

### createAuthorizationQuery ###
**Deprecated**,
Create OAuth parameters for query or entity body.

#### Arguments ####
- httpMethod : String
- uri : Uri
- realm : String
- consumerKey : String
- consumerSecret : String
- token : String
- tokenSecret : String
- signatureMethod : String
- callback : String
- verifier : String
- params : IEnumerable.[KeyValuePair.[String String]]

#### Return ####
String

### HMAC-SHA1 ###
Value: "HMAC-SHA1"

### RSA-SHA1 ###
Value: "RSA-SHA1"

YacqOAuth **does not support RSA-SHA1**.

### PLAINTEXT ###
Value: "PLAINTEXT"

**Auther did not test PLAINTEXT**.