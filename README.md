# bearskin-verifier

Bearskin is the name of my authentication service.
The main bearskin repository is currently private, but might become public some time in the future.

Bearskin generates a JWT token with some claims based on pre-stored information.
This is done when a login endpoint is called with a correct set of credentials.
The JWT token can only be generated by Bearskin service because it's the only one who knows the private key, but the tokens can be verified by anyone who got the public key.

This library will provide the functionality, and a structured way to verify a JWT token generated by Bearskin.
Other services can verify and retrieve the claims without the need of making a call to the Bearskin service.

Example:
```
claims, err := bearskin.GetClaimsFromVerifiedJwt(PUBLIC_KEY, JWT_TOKEN)
```
If the JWT token is invalid or there was a problem with the parsing, the `claims` will be `nil`, and an error will be returned.  
If the JWT token is valid, `claims` will be of type `bearskin.Claims` struct with the information from the token, and err will be `nil`.
