## What is a DID?
DID stands for decentralized identifier and refers to a w3c standard for uniquely referencing authentication information of a user. [Click here to know more about DID](https://www.w3.org/TR/did-core/).

## What is a key?

A key refers to a string of characters(bytes) that is used to cryptographically encrypt, decrypt, and sign data. There are two types of encryption algorithms; asymmetric (signature schemes) where there is a public key (encryption / signature verification key) and a secret key (decryption / signature signing key), and symmetric where a single key is used for encryption and decryption. 

## What is a signature?

A signature is a mathematical scheme for verifying the authenticity of digital documents. A valid digital signature gives a recipient (Verifier) strong reason to believe that the message (credential) was created by a known sender (Issuer) and that the message was not altered in transit (tamperproof).

## What is a Verifiable Credential?

A verifiable credential is a data artefact that codifies some information about the Holder, such as a test result or immunization record, that is attested (digitally signed) by an issuer, and is compliant with the w3c standard [Data Model](https://www.w3.org/TR/vc-data-model/) for constructing and signing verifiable credentials; signatures that allows the data to be verified.


## What is the role of blockchain?

The blockchain ledger acts as a decentralized registry of Issuers and their schemas, public keys, allowlist, blockedlist, and revocation registries. Trusted relationships can be established between a network of ledgers, allowing credentials to be widely accepted and transparently verified. No Holder DIDs or data is stored on the ledger. 
An organization needs to be registered on the IBM Digital Health Pass ledger, publishing a DID and a public key, before they can issue credentials that are verifiable by our system. 
When an organization receives a credential from a Holder, they can verify that credential by checking the issuer DID on the blockchain ledger, retrieving the public key and associated meta-data, and verifying the issuer signatures embedded into the credential.

## Why is data exchange trusted?

IBM Digital Health Pass is built on a decentralized identity architecture that combines both cryptographic trust at the machine layer and human trust at the business, legal, and social layers. 
Cryptographic trust is achieved through registration of Issuers on the blockchain ledger (DIDs, public keys, meta-data, …), with controls to prevent unauthorized tampering of data, and verification of signatures on the credentials exchanged between a Holder and Verifier.
Human trust is achieved through a transparent and well managed process for onboarding Issuers, including verifying identity and enforcing contractual obligations, so that a Verifier can trust an organization’s ownership of a specific DID and associated meta-data.

## What does decentralization mean?

There are two levels of decentralization that are most relevant in the context of IBM Digital Health Pass. Firstly, decentralization achieved through blockchain where verifiable credentials can be issued by Issuers registered on different ledgers and verified across blockchain networks. Secondly, decentralized achieved through peer-to-peer data exchange, where a data subject holds their data in their digital wallet and share with a Verifier on-demand. The Verifier can trust the presented data without needing to collect personal data in a centralized location, which is a target of cyberattack and presents technical and regulatory risk. 

## How does an organization issue a credential?

An organization is registered on the blockchain, where they publish their DID, public key, credential schemas, allowlists, blockedlist, and revocation lists. They can now package data according to one of their published schemas, cryptographically sign the data, and share with a data subject. The can be done locally with the Issuer or by using the platform’s Issue API. If using the Issue API, the Issuer can choose to obfuscate data locally before passing it to the Issue API. The IBM Digital Health Pass never persists any personally identifiable data, and only processes the data for the purposes of generating the signed and obfuscated verifiable credential.

## What is the digital wallet?

The IBM Digital Health Pass wallet is a mobile application that allows an individual to carry their data with them, so it's available whenever they need it, and to control what data they share, with whom, and for what purpose. It is built on an encrypted data vault and allows the Holder to manage their keys and identities, save and share credentials, track and manage consent, encrypt and decrypt data, conceal or reveal fields in their credentials to verifiers, respond to credential ownership  challenges, sign documents, and handle QR Codes.

## What is the verifier app?

The verifier app is a mobile application that an organization can install on a smartphone or tablet and use to scan a credential, shared by the data subject as a QR Code, and verify that it has been issued by a valid and trusted issuer, and that the data has not been tampered with. The verifier app can also issue identity challenges, which the Holder will sign, to obtain cryptographic assurance of the holder being the owner of the credential.


## How is the platform open?

Decentralized identity is, by their nature, decentralized and therefore it is critical that any such system supports integration across a network of ledgers and a network of credential issuers, verifiers, and holders. This is most effectively achieved through adoption of open standards and this is the approach of the IBM Digital Health Pass. The key objective of open integration is to allow credentials, and identities, issued through one blockchain network to be accepted and reliably verified by another blockchain network. This requires establishing a trust relationship between networks, since one blockchain consortia may not inspire the same level of trust as another or adopt the minimal required governance for specific use cases. 
There are several standards initiatives and open source projects that will help with open integration, some of which the platform has already adopted and others that are being explored.

**w3c DID Specification**

This specifies a common data model, a URL format, and a set of operations for decentralized identifiers (DIDs), DID documents, and DID methods. IBM Digital Health Pass has adopted this specification for the issuing and handling of DIDs.

**w3c Verifiable Credentials Data Model**

This specification provides a mechanism to express credentials in a way that is cryptographically secure, privacy respecting, and machine verifiable. IBM Digital Health Pass has adopted this specification for the issuing and verifying credentials.

**Trust over IP (ToIP) Foundation**

Part of the Linux Foundation, it is defining a complete architecture for Internet-scale digital trust that combines both cryptographic trust at the machine layer and human trust at the business, legal, and social layers. IBM is a member of this foundation and actively participating in this initiative.

**Decentralized Identity Foundation (DIF)**

This foundation is developing the foundational components of an open, standards-based, decentralized identity ecosystem for people, organizations, apps, and devices. IBM is one of the founding members.
