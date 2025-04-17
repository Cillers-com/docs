---
description: Setting Up A Free Trial API Gateway With Enterprise Features
---

# Kong Konnect

<figure><img src="../.gitbook/assets/image (1) (1).png" alt=""><figcaption></figcaption></figure>

### Integrate With Kong Konnect&#x20;

This setup gives you access to the ENTERPRISE-licenced AI plugins during the free trial.

Sign up at [https://konghq.com/products/kong-konnect/register](https://konghq.com/products/kong-konnect/register)

<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXdn6YPFR5ZlYlMZX7y9LwAN2K-MPkoJ1eDK_d39U8Bn8uAO4vk6vWfn1RY1knx41CiBKNhoAWbVaz7s73AApZkEioAjxL-h61QloZyEo_adrd__euOU_AmI_6ukbGcChDFXDhlW?key=jC8T-_XneVuC3ZQq8QXN1Z9t" alt=""><figcaption></figcaption></figure>

Click “Set up a Kong API Gateway”



<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXe2DjtwuDXzwwkNGuF0GJK-NMnblfwn0SA8L0g_qLUQ6E20LsiYlvKnC1mVPI8Q2XvRwPdwtyjzCCKqE_j8siXb7nuwGmQKU3rwdyrZOEK1dAM6i0jyrJfMt9-HNrPLNXupvyUb?key=jC8T-_XneVuC3ZQq8QXN1Z9t" alt=""><figcaption></figcaption></figure>

Select “Self-Managed Hybrid” and specify the name. Click “Next Step”



<figure><img src="https://lh7-rt.googleusercontent.com/docsz/AD_4nXfkZji9TNCJSmdnKnSQ6Z28ih_0UrRzUQ8f00xRox7NJjzdB0fwXPFL5yNZLLnBZI5pZ5J54FWBBzTrfu8ydRI0L_AL0DkTeSBmK7SRYArTeaWzX6qMN1NMJgZTen-HZIc-gBqjiA?key=jC8T-_XneVuC3ZQq8QXN1Z9t" alt=""><figcaption></figcaption></figure>

Select “Linux (Docker)” as the platform. Click “Generate certificate”.&#x20;



```yaml
  - { name: KONG_CLUSTER_CONTROL_PLANE, value: a6b7f53c23.us.cp0.konghq.com:443 }
  - { name: KONG_CLUSTER_SERVER_NAME, value: a6b7f53c23.us.cp0.konghq.com }
  - { name: KONG_CLUSTER_TELEMETRY_ENDPOINT, value: a6b7f53c23.us.tp0.konghq.com:443 }
  - { name: KONG_CLUSTER_TELEMETRY_SERVER_NAME, value: a6b7f53c23.us.tp0.konghq.com }- name: KONG_CLUSTER_CERT
  - name: KONG_CLUSTER_CERT
    value: |-
    -----BEGIN CERTIFICATE-----
    MIIxxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    xxx
    -----END CERTIFICATE-----
- name: KONG_CLUSTER_CERT_KEY
  value: |-
    -----BEGIN PRIVATE KEY-----
    MIGxxx
    xxx
    xxx
    xxx
    -----END PRIVATE KEY-----
 
```

Change the above env variables in the polytope.yml file in your project directory to the values generated. Certificates should of course be stored as secrets, but Polytope does not yet support multiline secrets, will be fixed soon.
