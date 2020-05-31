# Front-end for CoronaBot
- The chatbot can be found here: [CoViD19 Bot - AI4Bharat](https://covid19.ai4bharat.org/)

# Local setup

1. `npm i`
2. `npm run serve`

# Hosting on GCP

1. `npm install`
2. `npm run build`
3. `gcloud app deploy`(Optional)

# Setting up Gateway URL
1. In GCP project, create a service account for Diaglogflow API with full access and download it as JSON. 
2. Go to [Dialogflow Gateway Hosted by Ushakov](https://dialogflow.cloud.ushakov.co).
3. Signup and upload the Google cloud service JSON.
4. Click on "Manage" and copy the Gateway URL.
5. Paste the Gateway URL here.
```js
export default {
    gateway: 'https://dialogflow-web-v2.core.ushaflow.com'
    [...]
}
```

## [Code taken from](https://github.com/mishushakov/dialogflow-web-v2)
