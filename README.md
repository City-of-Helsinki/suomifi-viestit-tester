# suomifi-viestit-tester

Tester application for suomi.fi -viestit, for doing concrete testing against the service. This is
a very thin wrapper around the suomi.fi messaging REST API.

WARNING! Do not use this for any production purposes. There is barely any
error handling and no input sanitation whatsoever.

## Setup

You will need some sort of Python environment, this has been only tested
using a virtualenv. Basically

1. Setup & activate a virtualenv
2. pip install -r requirements.txt

## Initializing

No real UI exists, this is just a Python class for doing tests.

1. python
2. from suomifi_viestit_tester import SFMsgTester
3. m=SFMsgTester()
4. m.login("{your_suomifimsg_systemId}", "{your_suomifimsg_password}")

## Usage

### Send message example

Also see suomi.fi messaging API docs:
https://api.messages.suomi.fi/api-docs/

m.send_message("your_suomimsg_serviceId", "your_suomifi_testuser_personid", "{your subject}",
               "{your message test}", internal_id="{your_self_selected_internal_id", reply_allowed=True, verifiable=True)
