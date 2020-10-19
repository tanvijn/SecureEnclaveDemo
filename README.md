# SecureEnclaveDemo
## How to implement Secure Enclave in iOS App

SecureEnclaveDemo is an xcodeproject containing helper named as "SecEnclaveWrapper". You can use this wrapper in your project to encrypt/decrypt sensitive data using Secure Enclave.
The SecEnclaveWrapper class is using SecureEnclave to generate keys and use them to encrypt/decrypt sensitive data.
The SecureEnclave support is only available for iOS 10+.

We usually save data persistently in the app using UserDefaults, Keychain, Core Data or SQLite.
for ex- to save session of logged in user, we save username and password.

But this process puts our data at high security risk 

So its always recommended to store sensitive data in encrypted format. but again its a challange to secure keys used in encryption/decryption.

Well, here secure enclave comes in the role.

The Secure Enclave is a hardware-based key manager that’s isolated from the main processor to provide an extra layer of security. Using secure enclave we can create the key, securely store key, and perform operations with that key. Thus makes it difficult for the key to be compromised. Here we r using secure enclave in key generation and encryption/decryption.

## Difference between Keychain and Secure Enclave 

A Secure Enclave is a coprocessor fabricated within the system on chip. It uses encrypted memory and includes a hardware random number generator. As for the Keychain, the iOS Keychain provides a secure way to store these (passwords and other short but sensitive bits of data) items.
Keychain items are not stored inside Secure Enclave, they are stored inside a SQLite database on disk, but the encryption key needed to decrypt this data is inside the Secure Enclave. As for kSecAttrTokenIDSecureEnclave that apperas to be a flag that indicates that the key should be generated inside the Secure Element.
So Keychain doesn't use Secure Enclave automatically. Instead we have to implement code changes to leverage Secure Enclave. 

> If we are using the keychain to store a key which we can retrieve then the security level is not the same. We still have to move that key into memory to use it.

> Not having a mechanism to transfer key data into or out of the Secure Enclave is fundamental to its security.


For more detail please refer below documentations : 

https://developer.apple.com/documentation/security/certificate_key_and_trust_services/keys/storing_keys_in_the_secure_enclave

https://developer.apple.com/documentation/security/ksecattraccessibleafterfirstunlockthisdeviceonly
