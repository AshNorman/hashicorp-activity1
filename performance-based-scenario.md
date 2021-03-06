---
title: "Sample Scenario"
---

There is a single HashiCorp Vault cluster provisioned at the following IP address:

 ### `scenario-cluster-vault`:
- Vault Address: 127.0.0.1:8200
- Vault Token: s.f7Ea3C3ojOYE0GRLzmhSG

The AppRole auth method has been enabled on the approle/ path. A role has been created and has the following properties:

- Role Name: appy7
- Vault policy: policy7
- Roll ID: xxxxxxxx-xxxxxxxx-xxxxxxxx-xxxxxxxxxxx

Additionally, there is an application server which requires the use of the Vault Agent to retrieve and manage a Vault token to be stored in a local file. The Vault binary is already in the $PATH. The application server is called `scenario-node-appserver`.

### Application Server:

- Server Address: <IP_Address>
- Vault agent Config File: /etc/vault/agent7.hcl
- Sink Location: /etc/vault/token.json

Bucky is going to need to Securely configure Vault Agent Auto-Auth and Token Sink. Bucky has an application that needs to retrieve credentials from Vault, even though the application was not architected to interact directly with Vault. Bucky uses the Vault Agent to retrieve a Vault token and keep it renewed automatically. Using the information provided above, configure the application server to use the Vault Agent to retrieve a Vault Token. The Vault Agent should use approle for authentication, therefore a SecretID needs to be generated in Vault. When retrieving the token from vault, the resulting token should be protected using response wrapping on the Auth method. Write the token to the token.json file path. Important Note: you can validate the configuration by viewing the contents of the sink. If a token does not exist, the configuration is not correct.
