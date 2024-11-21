# suomifi-viestit-tester

Tester application for suomi.fi -viestit, for doing concrete testing against the service. This is
a very thin wrapper around the suomi.fi messaging REST API.

WARNING! Do not use this for any production purposes. There is barely any
error handling and no input sanitation whatsoever.

See suomi.fi messaging api docs for API details
https://api.messages.suomi.fi/api-docs/

Suomi.fi developer portal is good for general overview
https://kehittajille.suomi.fi/palvelut/viestit

## Setup

You will need some sort of Python environment, this has been only tested
using a virtualenv. Basically

1. Setup & activate a virtualenv
2. pip install -r requirements.txt
3. pip install ipython     # optional, but much nicer experience

## Initializing

No real UI exists, this is just a Python class for doing tests.

Note that "systemId" is your "username", you've received this from suomi.fi
while registering for the messaging service. You can have multiple
systemId, each with their associated serviceIds.

Also note that the messaging API is locked to the IP addresses you specified
while registering. You'll get an error, if you try to access the API from
any other address.

1. ipython   # you can also use just plain python
2. from suomifi_viestit_tester import SFMsgTester
3. m=SFMsgTester()
4. m.login("{your_suomifimsg_systemId}", "{your_suomifimsg_password}")

## Usage

### Send message example

"serviceId" is used to identify the sending service in messages received by citizens.
You received this together with systemId from suomi.fi.

m.send_message("your_suomimsg_serviceId", "your_suomifi_testuser_personid", "{your subject}",
               "{your message test}", internal_id="{your_self_selected_internal_id", reply_allowed=True, verifiable=True)
