# Serify

Serify is a wrapper around the Twilio Verify REST API. This simple and lightweight wrapper allows you to send and verify SMS codes with two easy to use methods – and only has one dependency. Both methods use async/await making it easy to integrate into your existing codebase.

## Example

To send a verification code using, use the `check` method as shown below:

```javascript
import Serify from 'serify';

const auth = new Serify({
	twilioServiceSid: 'YOUR_TWILIO_SERVICE_SID', // required
	twilioAccountSid: 'YOUR_TWILIO_ACCOUNT_SID', // required
	twilioAuthToken: 'YOUR_TWILIO_AUTH_TOKEN', // required
});

const send = async () => {
	try {
		const send = await auth.start({
			phone: 'USER_PHONE_NUMBER', // required
			country: 1, // optional
		});

		console.log(send);
	} catch (error) {
		console.log(error);
	}
};

send();
```

To verify a code, use the `verify` method as shown below:

```javascript
import Serify from 'serify';

const auth = new Serify({
	twilioServiceSid: 'YOUR_TWILIO_SERVICE_SID', // required
	twilioAccountSid: 'YOUR_TWILIO_ACCOUNT_SID', // required
	twilioAuthToken: 'YOUR_TWILIO_AUTH_TOKEN', // required
});

const verify = async () => {
	try {
		const verify = await auth.verify({
			phone: 'USER_PHONE_NUMBER', // required
			country: 1, // optional
			code: 'USER_VERIFICATION_CODE', // required
		});

		console.log(verify);
	} catch (error) {
		console.log(error);
	}
};

verify();
```

## Obtaining Tokens

Twilio can be confusing at times as the API requires an **Account Level SID**, an **Account Auth Token**, in addition to a **Service SID**. All tokens can be found on your dashboard.

1. The account level SID and Account Auth Token are provided at the top level of your account.
2. The service specific SID can be found when creating your application for the Twilio Verify product.
