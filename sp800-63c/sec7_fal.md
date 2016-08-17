<a name="fal"></a>

## 7. Federation Assurance Level (FAL)

This section defines allowable Federation Assurance Levels, or FAL. The FAL describes aspects of the assertion and federation protocol used in a given transaction. These levels can be requested by an RP or required by configuration of both RP and CSP for a given transaction. 

The FAL combines aspects of [federation model](#sec4), [assertion protection strength](#sec5), and [assertion presentation](#sec6) into a single, increasing scale. While many other combinations of factors are possible, this list is intended to provide clear implementation guidelines representing increasingly secure deployment choices. Each successive level subsumes and fulfills all requirements of lower levels. This table presents different requirements depending on whether the assertion is presented directly or indirectly. 

Such definitions not found in the FAL table are possible but outside the scope of this document.

|FAL|Direct Presentation Requirement|Indirect Presentation Requirement|
|:--:|----|----|
|1|Bearer assertion, asymmetrically signed by CSP|Bearer assertion, asymmetrically signed by CSP|
|2|Bearer assertion, asymmetrically signed by CSP|Bearer assertion, asymmetrically signed by CSP and encrypted to RP|
|3|Bearer assertion, asymmetrically signed by CSP and encrypted to RP|Bearer assertion, asymmetrically signed by CSP and encrypted to RP|
|4|Holder of key assertion, asymmetrically signed by CSP and encrypted to RP|Holder of key assertion, asymmetrically signed by CSP and encrypted to RP|

For example, FAL 1 maps to the OpenID Connect Implicit Client profile or the SAML Web SSO profile, with no additional features. FAL 2 maps to the OpenID Connect Basic Client profile or the SAML Artifact Binding profile, with no additional features. FAL 3 additionally requires that the OpenID Connect ID Token or SAML Assertion be encrypted to a public key representing the RP in question. FAL 4 requires the presentation of an additional key bound to the assertion (for example, a FIDO token) along with all requirements of FAL3.

Regardless of what is requested or required by the protocol, the applicable FAL is easily detected by the RP by observing the nature of the assertion as it is presented as part of the federation protocol. Therefore, the RP is responsible for determining which FALs it is willing to accept for a given authentication transaction and ensuring that the transaction meets the requirements of that FAL.


The following table lists strict adherence to M-04-04 Level of Assurance, mapping the corresponding Federation Assurance Levels. 

| Level of Assurance (LOA) |  Federation Assurance Level (FAL)
|:------------------:|:-----------------------------:
| 1 |  1
| 2 | 2
| 3 | 2
| 4 | 4

However, the table below shows the expanded set of FAL's that are allowable to meet M-04-04 Level of Assurance. Agencies SHALL select the corresponding FAL based on the assessed M-04-04 LOA.

| Level of Assurance | Federation Assurance Level
|:------------------:|:-----------------------------:
| 1 | 1, 2, 3, or 4 
| 2 | 2, 3, or 4
| 3 | 2, 3, or 4
| 4 | 3 or 4
