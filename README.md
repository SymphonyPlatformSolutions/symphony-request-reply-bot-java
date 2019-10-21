## Symphony Request/Reply Example Bot
This project serves as a hello world example to get started using the Symphony Java Client Library SDK.

## Requirements
* JDK 8+
* Maven 3

## Generate RSA Key Pair
```bash
mkdir rsa
cd rsa
openssl genrsa -out rsa-mybot-private-key.pem 4096
openssl rsa -in rsa-mybot-private-key.pem -pubout -out rsa-mybot-public-key.pem
```

## Create Service Account
1. Go to your pod's Admin and Compliance Portal (https://[my-company].symphony.com/?admin)
2. Create an Account > Service Account
3. Fill in desired bot username and other details
4. Paste in RSA public key from previous section
5. Create

## Configuration
Fill up `src/main/resources/config.json` with the appropriate values for pod information,
and service account details
```json5
{
    "sessionAuthHost": "[my-company].symphony.com",
    "sessionAuthPort": 443,
    "keyAuthHost": "[my-company].symphony.com",
    "keyAuthPort": 443,
    "podHost": "[my-company].symphony.com",
    "podPort": 443,
    "agentHost": "[my-company-agent].symphony.com",
    "agentPort": 443,

    "truststorePath": "certificates/all_symphony_certs_truststore",
    "truststorePassword": "changeit",

    "botUsername": "my-bot-username",
    "botEmailAddress": "my-bot-email@my-company.com",

    "botPrivateKeyPath": "rsa/",
    "botPrivateKeyName": "rsa-mybot-private-key.pem",

    "botCertPath": "",
    "botCertName": "",
    "botCertPassword": "",

    "proxyURL": "",
    "proxyUsername": "",
    "proxyPassword": "",
    "keyManagerProxyURL": "",
    "keyManagerProxyUsername": "",
    "keyManagerProxyPassword": ""
}
```

## Debug
### Using IDE
Debug using standard Eclipse/IntelliJ Launch Configuration

### Using Command Line
```bash
mvn install dependency:copy-dependencies
java -cp target/dependency/*:target/classes RequestReplyBot
```
