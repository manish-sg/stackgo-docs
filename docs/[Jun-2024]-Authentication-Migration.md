---
stoplight-id: nzdn73kxnmuei
---

# StackGo API Platform Upgrade: Simplifying Authentication with API Keys

We’re excited to announce a significant update to the StackGo API platform. To streamline our authentication process and improve ease of use, we are moving from the Auth0 OAuth client credentials process to an API key process.

## What’s Changing?

Previously, StackGo relied on the Auth0 OAuth client credentials process for authentication. While robust, this method required token cycles and expirations, adding complexity to the development workflow.

With our new API key process, the authentication header will now consist of the `client_id:client_secret` encoded in Base64. This change eliminates the need for token management, making your integration with StackGo more straightforward and efficient.

## How It Works

To authenticate your API requests with the new system, follow these simple steps:

1.	Obtain Your API Key: Retrieve your client_id and client_secret from the StackGo developer portal.
2.	Encode in Base64: Encode your `client_id:client_secret` pair in Base64.
3.	Add to Header: Include the encoded string in your API request header.

Here are examples in Python, Java, and JavaScript:

### Code Examples (Python, Java, Node)

````python
import base64
import requests

client_id = 'your_client_id'
client_secret = 'your_client_secret'
credentials = f'{client_id}:{client_secret}'
encoded_credentials = base64.b64encode(credentials.encode()).decode()

headers = {
    'Authorization': f'Basic {encoded_credentials}'
}

response = requests.get('https://api.stackgo.com/your-endpoint', headers=headers)
print(response.json())
````

```java
import java.util.Base64;
import java.net.HttpURLConnection;
import java.net.URL;

public class StackGoClient {
    public static void main(String[] args) {
        String clientId = "your_client_id";
        String clientSecret = "your_client_secret";
        String credentials = clientId + ":" + clientSecret;
        String encodedCredentials = Base64.getEncoder().encodeToString(credentials.getBytes());

        try {
            URL url = new URL("https://api.stackgo.com/your-endpoint");
            HttpURLConnection connection = (HttpURLConnection) url.openConnection();
            connection.setRequestProperty("Authorization", "Basic " + encodedCredentials);

            int responseCode = connection.getResponseCode();
            System.out.println("Response Code: " + responseCode);
            // Add further handling of the response as needed
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}

```


```javascript
const clientId = 'your_client_id';
const clientSecret = 'your_client_secret';
const credentials = `${clientId}:${clientSecret}`;
const encodedCredentials = btoa(credentials);

const headers = new Headers();
headers.append('Authorization', `Basic ${encodedCredentials}`);

fetch('https://api.stackgo.com/your-endpoint', { headers: headers })
    .then(response => response.json())
    .then(data => console.log(data))
    .catch(error => console.error('Error:', error));

```

## Benefits

Benefits

- Simplicity: No more managing token lifecycles or handling expirations.
- Efficiency: Faster and easier integration with StackGo APIs.
- Security: Secure and straightforward authentication using Base64 encoding.


## Transition Timeline

We encourage all developers to transition to the new API key authentication process as soon as possible. Support for the Auth0 OAuth client credentials process will be phased out over the next few months.

For detailed documentation and support, visit our API documentation.

We believe this update will enhance your experience with StackGo, making it easier than ever to build and integrate with our platform. If you have any questions or need assistance, our support team is here to help.

Thank you for being a valued part of the StackGo community. We look forward to seeing the amazing things you’ll build with our API.

Happy coding!

Feel free to reach out with any feedback or suggestions as we continue to improve StackGo.