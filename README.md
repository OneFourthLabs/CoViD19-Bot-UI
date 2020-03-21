# Front-end for CoronaBot

# Local setup

1. `npm i`
2. `npm run serve`

# Hosting on GCP

1. `npm install`
2. `npm run build`
3. `gcloud app deploy`(Optional)

# Setting up Gateway URL
1. Go to [Dialogflow Gateway Hosted by Ushakov](https://dialogflow.cloud.ushakov.co).
2. Signup and upload the Google cloud service JSON.
3. Click on "Manage" and copy the Gateway URL.
4. Paste the Gateway URL here.
```js
export default {
    gateway: 'https://dialogflow-web-v2.core.ushaflow.com'
    [...]
}
```

[Code taken from]https://github.com/mishushakov/dialogflow-web-v2
