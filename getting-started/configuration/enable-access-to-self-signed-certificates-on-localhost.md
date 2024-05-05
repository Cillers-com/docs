# Enable Access To Self-Signed Certificates On Localhost

The Cillers stack is secured with https connections by default. But, to simplify development on your local development machine, e.g. laptop, you can disable certificate validations for localhost connections. Otherwise, you will need to set up and manage certificates on your development machine which can be a lot of work and offers no benefits for most scenarios.&#x20;

There are two applications that you need to do this in: your browser and your API client UI applications. Here are instructions for how to do this in our preferred browser, Chrome, and our preferred API client UI application, Insomnia. &#x20;

### Insomnia

Uncheck "Validate certificates" in Insomnia's Settings.&#x20;

<figure><img src="../../.gitbook/assets/image (1) (1) (1) (1).png" alt="" width="227"><figcaption></figcaption></figure>

<figure><img src="../../.gitbook/assets/image (1) (1) (1).png" alt="" width="190"><figcaption></figcaption></figure>

### Chrome

Go to [chrome://flags/#allow-insecure-localhost](chrome://flags/#allow-insecure-localhost) and click enable.&#x20;

<figure><img src="../../.gitbook/assets/image (4) (1).png" alt=""><figcaption></figcaption></figure>
