# Generate JSON Web Token (JWT)

The Generate JWT policy can be used in IBM API Connect to generate a JSON Web Token.

## Prerequisites

  - IBM API Connect 5.0
  - IBM DataPower 7.5 with the Application Optimization (AO) option
  - Crypto object(s), if used, located in the IBM API management domain on the DataPower appliance
    - The crypto object(s) must reference the Shared Secret Key or certificate necessary to encrypt or sign the JWT contents.
  - JSON Web Key (JWK), if used,  must be referenced by a runtime variable
  
## Usage

  - For algorithm types HS256, HS384, and HS512 the Crypto Object referenced must be a Shared Secret Key
  - For algorithm types RS256, RS384, RS512, ES256, ES384 and ES512 the Crypto Object referenced must be a Crypto Key (private key)
  - The crypto material may be provided via a JSON Web Key (JWK)
  - If both crypto object and JWK are specified crypto object will be used
    
## Properties
   
  - jwt
   -- Runtime variable in which to place the generated JWT
   -- generated jwk also written to response body
  - iss-claim
   -- Runtime variable from which from which a string representing the Principal (iss) that issued the JWT can be retrieved
   -- The issuer claim, 'iss', identifies the principal that issues the JWT
  - sub-claim
   -- Runtime variable from which a string representing the Subject (sub) Claim can be retrieved
  - exp-claim
   -- The validity period (in seconds) for calculating the JWT expiration time, 'exp' claim of the JWT
  - aud-claim
   -- Runtime variable from which the Audience (aud) Claim string can be retrieved. 
   -- Multiple are set via a comma separated string
  - private-claims
   -- Specify the variable name from which a valid JSON set of private claims can be retrieved
  - jws-jwk
   -- Runtime variable containing JWK to be used to sign the JWT
  - jws-alg
   -- Select a cryptographic algorithm
       - HS256
       - HS384
       - HS512
       - RS256
       - RS384
       - RS512
       - ES256
       - ES384
       - ES512
  - jws-crypto
   -- Specify the crypto object used to sign the message
  - jwe-enc
   -- Select an encryption algorithm
       - A128CBC-HS256
       - A192CBC-HS384
       - A256CBC-HS512
  - jwe-jwk
   -- Runtime variable containing JWK to be used to encrypt the JWT
  - jwe-alg
   -- Key encryption algorithm
       - RSA1_5
       - RSA-OAEP
       - RSA-OAEP-256
       - A128KW
       - A192KW
       - A256KW      
  - jwe-crypto
   -- Specify the crypto object used to encrypt the message
   
