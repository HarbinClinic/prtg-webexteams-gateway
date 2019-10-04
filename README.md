# prtg-webexteams-gateway
An Azure Function to enable notifications from PRTG to Webex Teams

## Setup

### Webex Teams

Visit App Hub to add a Webhook name to an existing space and make note of the Webhook URL once added. 

### Azure

For information on creating the Azure Function, please see the following link:

[Create an HTTP triggered function in Azure](https://docs.microsoft.com/en-us/azure/azure-functions/functions-create-first-function-python)

1. Clone this repository and replace the default Function's __init__.py. 
2. Populate the WEBEX_WEBHOOK_URL constant with the Webhook URL from App Hub.
3. Deploy the modified function.
4. Add a Function Key to protect the Function abuse and make note of the key.

### PRTG

1. Add a new Notification Template.
2. Enable Execute HTTP Action.
3. Populate the URL with your Azure Function URL and key.
4. Select Post for the HTTP Method.
5. Add a text or markdown payload using standard PRTG variables. Below is an example.
   ```
   markdown=%datetime | [%device](%linkdevice) [%name](%linksensor) %status %down (%message) 
   ```
6. Send a test notificaiton. 
