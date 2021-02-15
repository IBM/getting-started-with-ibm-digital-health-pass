# Getting started with IBM Digital Health Pass


## Introduction

How do we bring people back to physical locations such as the workplace or airports without compromising on safety protocols. How do we ensure the information being shared are secure. IBM Digital health pass can help with all of these requirements & more.


## Overview

IBM Digital Health Pass (IDHP) is an open standards-based platform that allows secure, privacy-preserving, and verifiable exchange of data between organizations and their patients, employees, customers, and citizens, to drive agile and responsive businesses. Data is exchanged as verifiable credentials that, in combination with sophisticated cryptographic and obfuscation techniques, makes data tamperproof so that it can be trusted by all parties.

Click [here](https://www.ibm.com/products/digital-health-pass) to know more about IBM Digital Health Pass.


## Estimated time

It would take about 45 minutes to complete this tutorial.


## Prerequisites 

*	Obtain Access to IBM Digital Health Pass
*	Get Registered & Onboarded
*	Access IBM Digital Health Pass APIs and download IBM Digital Health Pass Wallet and IBM  Digital Health Pass Verify mobile applications


## Steps

1. [Authorize the user](#1-authorize-the-user)
1. [Choose a Schema](#2-choose-a-schema )
1. [Issue a credential](#3-issue-a-credential)
1. [Verify a credential](#4-verify-a-credential)
1. [Manage credentials](#5-manage-credentials)


### 1. Authorize the user

Login to the Healthpass API in the Swagger UI per below using your credentials and hit `Execute`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/login-hp-api.png)

Copy the access token excluding the double quotation marks, click on `Authorize`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/authorize.png)

Paste the access token from the previous step under `Value`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/access-token.png)

Hit `Authorize` & `Close` and you are now authorized to make API calls.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/authorized.png)


###  2. Choose a Schema

`You can query existing schemas or create your own as per the below steps.`

To query existing schemas, follow these steps.

Navigate to `schemas Manage schemas` section in the Swagger UI, click on `GET/schemas Get schemas` & hit `Try it out`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/query-sch.png)

Update the `Issuer ID` field and hit `Execute`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/get-sch.png)

Upon successful execution of the query, you will see the message per below with the retrieved schema information which can also be downloaded onto your local file system.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/retrieved-sch.png)

To create a new schema, follow these steps.

Navigate to `schemas Manage schemas` section in the Swagger UI, click on `POST /schemas Create schema` & hit `Try it out`

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/schemas.png)

Update the details in the text boxes and hit `Execute`. Server response should return with the code `200` to confirm successful execution. 

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/schema-created.png)

A sample `Temperature Scan` schema would look like below.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/get-sch-1.png)
![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/get-sch-2.png)
![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/get-sch-3.png)


### 3. Issue a credential


Navigate to `credentials Manage credentials` section in the Swagger UI and hit `Try it out`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/cred.png)

Update the fields like Issuer ID, Credential type (string or encoded), Output type (string or qrcode) and hit `Execute`.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/cred-execute.png)

A sample `temperature` credential `(string format)` would look like below.

![](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/temp-cred.png)

A sample `temperature` credential `(qrcode format)` would look like below to be verified by the app in subsequent steps.

<img src="https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/images/cred-qrcode.png" width="250" height="250">


### 4. Verify a credential

In order to verify a credential, your application will need to be able to read a credential (QR Code or file) and verify it. Verification minimally involves looking up the ledger to: 
1) Check that the Issuer DID is a valid and trusted one (the issuer DID is in the credential) 
2) Retrieve the DID document which contains the public key used for verifying signatures.
3) Retrieve the schema of the credential (the schema DID is in the credential)
4) Check that the credential has not been revoked (the credential DID is in the credential, and will be in the revocation registry if it's been revoked)

Once you have all this data in your application, you can then run the verification logic, which can vary depending on your application requirements, but minimally requires:
1) Checking the credential is not expired (expiryDate in credential).
2) Checking the credential is not revoked (already done in the ledger lookup)
3) Checking the credential signature block (using PK retrieved from ledger)
4) Check any application-specific logic, such as verifying identity, checking field values, etc.

In a future tutorial, we will explain in more detail how verification works, including providing code samples. To get started quickly, you can download the verifier app from the appstore. It allows you to scan a QR Code and verifies the credential. In the demo video in the next section, you can see the verifier app at work.

### 5. Manage credentials 

If you are looking to build a wallet directly into your existing mobile application, then there are a few things that you will minimally need to consider:
1) Secure storage of the wallet data
2) Loading a credential into a wallet, such as scanning a QR Code, and performing verification before loading it.
3) Providing a credential viewer, so the Holder can view the data in the credential.
4) Generating a QR Code to allow the Holder to share the credential with a 3rd Party.

In a future tutorial, we will explain in more detail how credentials can integrated into existing mobile applications. To get started quickly, you can download the wallet app from the appstore. It allows you to scan a QR Code to load a credential into your wallet, verifies the credential, saves it in your wallet, allows you to view the details, and generate a QR Code to share with a third party. 

In the video below, you can see the wallet at work.

[![](http://img.youtube.com/vi/Jr0rGjJhjL0/0.jpg)](https://youtu.be/Jr0rGjJhjL0)


## Summary

In this tutorial, we have learned about IBM Digital Health Pass and also explored features like creating schema, issuing credentials using the IDHP API which can be integrated into different applications to build end to end solution effectively. If you have more questions feel free to visit our [FAQs](https://github.com/IBM/getting-started-with-ibm-digital-health-pass/blob/main/FAQs.md) section to get the details. 
