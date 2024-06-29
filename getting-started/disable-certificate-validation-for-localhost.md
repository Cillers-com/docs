# Disable Certificate Validation For Localhost

The Cillers stack is secured with https connections by default. But, to simplify development on your local development machine, e.g. laptop, you can disable certificate validations for localhost connections. Otherwise, you will need to set up and manage certificates on your development machine which can be a lot of work and offers no benefits for most scenarios.&#x20;

There are two applications that you need to do this in: your browser and your API client UI applications. Here are instructions for how to do this in our preferred browser, Chrome, and our preferred API client UI application, Insomnia. &#x20;

### Chrome

Start the Chrome application and paste the following URL in the address bar: "chrome://flags/#allow-insecure-localhost" and click enable.&#x20;

<figure><img src="../.gitbook/assets/image (4) (1) (1).png" alt=""><figcaption></figcaption></figure>

### Kong Insomnia

Start the Kong Insomnia application and click on Preferences in the bottom left corner. Turn off the "Validate certificates" and "Validate certificates during authentication" settings. &#x20;

<figure><img src="../.gitbook/assets/image (13).png" alt="" width="332"><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/image (14).png" alt="" width="375"><figcaption></figcaption></figure>





