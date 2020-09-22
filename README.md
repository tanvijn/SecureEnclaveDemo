# SecureEnclaveDemo
How to implement Secure Enclave in iOS App
we usually save data persistently in the app using UserDefaults, Keychain, Core Data orSQLite.
for ex- to save session of logged in user, we save username and password.

But this process puts our data at high securrity risk 

So its always recommended to store sensitive data in encrrypted format. but again its a challange to secure keys used in encryption/decryption.

Well, here secure enclave comes in d role 

The Secure Enclave is a hardware-based key manager that’s isolated from the main processor to provide an extra layer of security. Using secure enclave we can create the key, securely store key, and perform operations with that key. Thus makes it difficult for the key to be compromised. Here we r using secure enclave in key generation and encrypt/decryptn.



For more detail please refer below documentation : 

https://developer.apple.com/documentation/security/certificate_key_and_trust_services/keys/storing_keys_in_the_secure_enclave

https://developer.apple.com/documentation/security/ksecattraccessibleafterfirstunlockthisdeviceonly
