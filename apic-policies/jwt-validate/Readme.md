# Validate JSON Web Token (JWT)

The Validate JWT policy can be used in IBM API Connect to validate a 
JSON Web Token.

## Prerequisites

  - IBM API Connect 5.0
  - IBM DataPower 7.5 with the Application Optimization (AO) option
  - Crypto object(s) located in the IBM API management domain on the DataPower 
    appliance
    - The crypto object(s) must reference the Shared Secret Key or public cert
      necessary to decrypt the JWT contents or verify the signature.
  - JSON Web Key (JWK) must be referenced by a runtime variable
  
## Usage

  - If the original message was signed with a Shared Secret Key, the Crypto 
    Object specified must be a Shared Secret Key
  - If the original message was signed with a private Key, Crypto Object 
    specified must be a Crypto Certificate (public certificate)
  - The crypto material may be provided via a JSON Web Key (jwk)
  - If both crypto object and JWK are specified crypto object will be used  
  - Subsequent actions can access the full set of claims via the output-claims
    runtime variable to validate any additional claims
    
## Properties

  - jwt 
   -- Context or runtime variable containing JWT to be validated
   -- default: request.headers.authorization
  - output-claims
   -- Runtime variable to which the JSON set of all decoded claims will be assigned
   -- default: decoded.claims
  - iss-claim
   -- PCRE used to validate the Issuer (iss) Claim
  - aud-claim
   -- PCRE used to validate the Audience (aud) Claim
  - jwe-crypto
   -- Name of crypto object used to decrypt the message
  - jwe-jwk
   -- Runtime variable containing JWK to be used to decrypt the JWT
  - jws-crypto
   -- Name of crypto object used to verify the signature
  - jws-jwk
   -- Runtime variable containing JWK to be used to verify the signature
