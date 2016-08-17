<a name="sec4"></a>

## 4. Digital Authentication Model

### <a name="4-1"></a>4.1. Overview

[OMB M-04-04](#M-04-04) にあるとおり, Digital Authentication はある Digital System に提示された個人の Identity に対して確信を得るプロセスである.
各システムは Authenticated Identity を元に, 当該個人が当該オンライントランザクションを実行する権限を持っているかどうかを判断する.
多くの場合, Authentication およびトランザクションは Internet のようなオープンネットワーク上で実施されるが, ネットワークアクセスが制限されており, その制限を考慮したアクセスコントロールがなされる場合もある.

<!-- In accordance with [OMB M-04-04](#M-04-04), digital authentication is the process of establishing confidence in individual identities presented to a digital system. Systems can use the authenticated identity to determine if that individual is authorized to perform an online transaction. In most cases, the authentication and transaction take place across an open network such as the Internet; however, in some cases access to the network may be limited and access control decisions may take this into account. -->

本ガイドラインにおける Digital Authentication Model は, 政府機関で現在用いられている技術およびアーキテクチャを反映したものになっている.
Credential の発行と Attribute の提供が異なる主体によって行われるなど, 複数の主体に機能が分離されたより複雑なモデルも考えられ, ある種のアプリケーションではそういったモデルを採用するメリットがあるだろう.
本ドキュメントではシンプルなモデルを扱うが, これは決して各機関が機能分離モデルの採用を排除するものではない.
また, 本来 Credential Service Provider (CSP) が実施する登録, Identity Proofing, 発行プロセスにおいても, それらのプロセスが Registration Authority (RA) や Identity Manager (IM) と呼ばれる主体に移譲されることもある.
通常は RA/IM と CSP の間には強い関連性があるが, これらの関連の性質は個々のケースで異なり得る.
RA/IM と CSP の関連性やその要件については本ドキュメントのスコープ外とする.
以降では, CSP は RA/IM の機能を含むものとして進める.

<!-- The digital authentication model used in these guidelines reflects current technologies and architectures used in government. More complex models that separate functions, such as issuing credentials and providing attributes, among larger numbers of parties are also available and may have advantages in some classes of applications. While a simpler model is used in this document, it does not preclude agencies from separating these functions. In addition, certain enrollment, identity proofing, and issuance processes performed by the credential service provider (CSP) are sometimes delegated to an entity known as the registration authority (RA) or identity manager (IM). A close relationship between the RA/IM and CSP is typical, and the nature of this relationship may differ among RAs, IMs, and CSPs. The types of relationship and their requirements is outside of the scope of this document.  Accordingly, the term CSP will be used to be inclusive of RA/IM functions. -->

Digital Authentication は登録のフェーズから開始される.
一般的な登録プロセスは次のような手順となる.
Applicant が CSP に登録申請を行う.
申請が認められると, CSP は Credential を生成し, それを1つ以上の Authenticator に紐付ける.
Credential には Identifier (仮名可) が含まれており, CSP が検証した1つ以上の属性が含まれることもある.
Authenticator は CSP が発行することもあれば, Subscriber が直接生成・提示することもあり, 3rd-party が提供することもある.
Authenticator と Credential はそれ以降の Authentication Event で用いられる.

<!-- Digital authentication begins with enrollment. The usual sequence for enrollment proceeds as follows. An applicant applies to a CSP. If approved, the CSP creates a credential and binds it to one or more authenticators. The credential includes an identifier, which can be pseudonymous, and possibly one or more attributes that the CSP has verified. The authenticators may be issued by the CSP, generated/provided directly by the subscriber, or provided by a third party. The authenticator and credential may be used in subsequent authentication events. -->

Applicant が彼らの実世界の Identity と紐付いていることを検証するプロセスが *Identity Proofing* である.
Identity Proofing の強度は Identity Assurance Level (IAL) としてカテゴライズされている.
IAL1 では Identity Proofing は要求されない.
IAL2 および IAL3 では Identity Proofing が要求されるが, CSP は検証済の属性値や Claim, 仮名等をアサートしても良いし, 何もアサートしなくてもよい.
これらの情報は, Relying Party (RP) がアクセスコントロールや認可判断を行うときに有用である.
RP は彼らが必要とする IAL を2ないし3とした上で, 特定の属性のみを必要とすることもあり, また当該個人を特定しない程度の属性のみを必要とすることもある.
こういったケースでは必要な属性のみを要求することでプライバシーを高めることができるが, これは Proofing Process の強度を Authentication Process の強度と分離して定義したことで得られたメリットの1つである.
RP は Identity Proofing, Attribute Collection, Attribute Storage をすべて CSP にゆだねる Federated Identity というアプローチをとることもできる.

<!-- The process used to verify an applicants association with their real world identity is calld *identity proofing*. The strength of identity proofing is described by a categorization called the identity assurance level (IAL). At IAL 1, identity proofing is not required, therefore any attribute information provided by the subscriber is self-asserted and not verified. At IAL 2 and 3, identity proofing is required, but the CSP may assert verified attribute values, verified attribute claims, pseudonymous identifiers, or nothing. This information assists Relying Parties (RPs) in making access control or authorization decisions. RPs may decide that their required IAL is 2 or 3, but may only need specific attributes, and perhaps attributes that retain an individual's pseudonymity. This privacy enhancing approach is one of the benefits of separating the strength of the proofing process from that of the authentication process. A relying party may also employ a federated identity approach where the RP outsources all identity proofing, attribute collection, and attribute storage to a CSP. -->

本ドキュメントでは, 認証される主体を Claimant, Identity を検証する主体を Verifier と呼ぶ.
Authentication Protocol を通じて Claimant が1つ以上の Authenticator を所有および管理していることを Verifier に示すことで, Verifier は Claimant が正規の Subscriber であることを検証できる.
その後 Verifier は Subscriber に関する Assertion を RP に送る.
Subscriber は仮名 (Pseudonymous) な場合もあれば仮名でない場合もある.
当該 Assertion は Subscriber の識別子を含むと同時に, 氏名や登録時に検証されたその他の属性といった Identity 情報を含むこともある.
(詳細は CSP のポリシーとアプリケーションのニーズに依存する)
Verifier が RP をかねる場合, Assertion は Implicit なこともある.
RP は Verifier が提供した Authenticated Information をもとに, Access Control や Authorization Decision を行うことができる.

<!-- In this document, the party to be authenticated is called a claimant and the party verifying that identity is called a verifier. When a claimant successfully demonstrates possession and control of one or more authenticators to a verifier through an authentication protocol, the verifier can verify that the claimant is a valid subscriber. The verifier passes on an assertion about the subscriber, who may be either pseudonymous or non-pseudonymous, to the RP. That assertion includes an identifier, and may include identity information about the subscriber, such as the name, or other attributes that were verified in the enrollment process (subject to the policies of the CSP and the needs of the application). Where the verifier is also the RP, the assertion may be implicit. The RP can use the authenticated information provided by the verifier to make access control or authorization decisions. -->

Authentication は Claimant Identity の確からしさを確立し, 場合によっては Claimant Attributes に関しても確からしさを確立する.
(例えば, Subscriber が US Citizen であるとか, 特定の大学の学生であるとか, ある機関や組織から特定の番号やコードを割り振られているなど)
Authentication は Claimant が認可されているかやアクセス権を持つかなどを判断するものではなく, それらはまた別の話である.
RP (例: 政府機関) は Subscriber の Authenticated Identity および Attributes をもとに, その他の要素も含めて, Access Control や Authorization Decision を行う.
本ドキュメントは RP が Subscriber を認証した後に追加の情報を要求することを禁止するものではない.

<!-- Authentication establishes confidence in the claimant’s identity, and in some cases in the claimant’s attributes (for example if the subscriber is a US Citizen, is a student at a particular university, or is assigned a particular number or code by an agency or organization). Authentication does not determine the claimant’s authorizations or access privileges; this is a separate decision. RPs (e.g., government agencies) will use a subscriber’s authenticated identity and attributes with other factors to make access control or authorization decisions. Nothing in this document precludes RPs from requesting additional information from a subscriber that has successfully authenticated. -->

Authentication Process の強度は Authenticator Assurance Level (AAL) として記述される.
AAL1 は Single-factor Authencitacion を要求し, 多様な Authenticator の利用を認めている.
AAL2 は AAL1 に加えて2つ目の Authentication Factor を要求している.
もっともレベルの高い AAL3 では, AAL2 の片方の Factor として, ハードウェアベースの Authenticator の利用を要求している.

<!-- The strength of the authentication process is described by a categorization called the authenticator assurance level (AAL). AAL 1 requires single-factor authentication and is permitted with a variety of different authenticator types. At AAL 2, authentication requires two authentication factors for additional security. Authentication at the highest level, AAL 3, requires the use of a hardware-based authenticator and one other factor. -->

Authentication の一環として, Device Identity や Geo-location などのメカニズムを利用し, 誤判定を検知 / 防止することもある.
これらのメカニズムは Authenticator Assurance Level を直接引き上げるものではないが, Security Policy やリスク逓減策として利用できる.
多くの場合, Authentication Process および Authentication Service は多くのアプリケーションや機関に共有されることになるが, 特定のアプリケーションの要件に基づいてアクセス許可やトランザクション実施の判断を行うのは, RP となる個々の機関やアプリケーションである.

<!-- As part of authentication, mechanisms such as device identity or geo-location may be used to identify or prevent possible authentication false positives. While these mechanisms do not directly increase the authenticator assurance level, they can enforce security policies and mitigate risks. In many cases, the authentication process and services will be shared by many applications and agencies. However, it is the individual agency or application acting as the RP that shall make the decision to grant access or process a transaction based on the specific application requirements. -->

[Figure 1](#Figure1) は, Digital Authentication Model に関与する多様な主体およびそれらの間のインタラクションを描いている.
左側は登録, Credential 発行, Lifecycle Management, 個人が Identity Proofing および Authentication の各フェーズで取りうるステータスを示している.
一般的には以下のような一連のインタラクションが行われる.

<!-- The various entities and interactions that comprise the digital authentication model used here are illustrated below in [Figure 1](#Figure1). The left shows the enrollment, credential issuance, lifecycle management activities, and the various states an individual transitions to based on the phase of identity proofing and authentication they are in. The usual sequence of interactions is as follows: -->

1. 個人 (Applicant) が登録プロセスを通じて CSP に申し込みを行う.
2. CSP は Applicant に対して Identity Proofing を行い, Proofing が成功すれば Applicant は Subscriber となる.
3. CSP と新規 Subscriber の間で, Authenticator およびそれに対応する Credential が確立される.
4. CSP は (最低限) 当該 Credential 自体, 当該 Credential のステータス, 当該 Credential が有効な間に登録されたデータを管理する. Subscriber は自身の Authenticator を管理する.

<!-- 1.	An individual (applicant) applies to a CSP through an enrollment process.
2.	The CSP identity proofs that applicant. Upon successful proofing, the applicant becomes a subscriber.
4.	An authenticator and a corresponding credential are established between the CSP and the new subscriber.
5. The CSP maintains the credential, its status, and the enrollment data collected for the lifetime of the credential (at a minimum). The subscriber maintains his or her authenticator. -->

これ以外のフローは上記ほど一般的ではないであろうが, 同じ要件を満たす別のやり方も存在しうる.

<!-- Other sequences are less common, but could also achieve the same functional requirements. -->

[Figure 1](#Figure1) の右側は, Authenticator を利用して Digital Authentication を行う各主体およびそれらの間でのインタラクションを描いている.
トランザクション実施のために　Subscriber の認証が必要な時には, Subscriber は Verifier に対する Claimant となり, 以下のようなインタラクションを行うことになる.

<!-- The right side of [Figure 1](#Figure1) shows the entities and the interactions related to using a authenticator to perform digital authentication. When the subscriber needs to authenticate to perform a transaction, he or she becomes a claimant to a verifier. The interactions are as follows: -->

1. Claimant は自身の Authenticator を所有および管理していることを Authentication Protocol を通じて Verifier に示す.
2. Verifier や CSP とインタラクションをおこない, Subscriber Identity と Authenticator を紐付ける Credential の検証を行う. また同時に CSP から Claimant の属性を取得することもある.
3. Verifier が RP と別の主体の場合, Verifier は RP に対して Subscriber に関する Assertion を提供する. RP は Assertion に含まれる情報を使って Access Control や Authorization Decision を行う.
4. Subscriber と RP の間で認証済セッションが確立される.

<!-- 1.	The claimant proves to the verifier that he or she possesses and controls the authenticator through an authentication protocol.
2.	The verifier interacts with the CSP to validate the credential that binds the subscriber’s identity to his or her authenticator and to optionally obtain claimant attributes.
3.	If the verifier is separate from the RP (application), the verifier provides an assertion about the subscriber to the RP, which may use the information in the assertion to make an access control or authorization decision.
4.	An authenticated session is established between the subscriber and the RP. -->

いかなる場合でも, RP は Claimant の認証前に必要な属性を CSP に要求するべきである.
また Claimant は, Assertion の生成・提供前に, それらの属性提供に対する同意を求められるべきである.

<!-- In all cases, the RP should request the attributes it requires from a CSP prior to authentication of the claimant.  In addition, the claimant should be requested to consent to the release of those attribute prior to generation and release of an assertion. -->

場合によっては, Verifier は CSP とリアルタイムにコミュニケーションを行う必要がないこともある. (例: デジタル証明書を利用する場合など)
したがって Verifier と CSP の間の点線は, それら2つの主体の間の (物理的というより) 論理的なリンクを示すものである.
実装によっては Verifier, RP, CSP は [Figure 1](#Figure1) のようにそれぞれ分離・独立していることもあるが, それらが同じプラットフォーム上にある場合, それらの要素間のインタラクションは (Untrusted Network を介したやりとりではなく) 同じシステム上のアプリケーション間のローカルメッセージとなる.

<!-- In some cases, the verifier does not need to communicate in real time with the CSP to complete the authentication activity (e.g., some uses of digital certificates). Therefore, the dashed line between the verifier and the CSP represents a logical link between the two entities rather than a physical link. In some implementations, the verifier, RP and the CSP functions may be distributed and separated as shown in [Figure 1](#Figure1); however, if these functions reside on the same platform, the interactions between the components are local messages between applications running on the same system rather than protocols over shared untrusted networks. -->

前述の通り, CSP は自身が発行した Credential のステータスを管理する.
一般的に CSP は Credential の管理期間を限定するため Credential 発行時にその有効期限を定める.
ステータスが変更されたり Credential が有効期限切れに近づくと, Credential は更新されたり再発行されることもあれば, 無効化されたり破棄されることもある.
典型的には, Subscriber が自身の既存かつ有効期限切れでない Authenticator および Credential を使って CSP に対して認証を行い, 新規 Authenticator および Credential の発行を要求することになる.
Subscriber が Authenticator および Credential の期限切れないし無効化前に再発行できなかった場合は, 登録プロセスをやり直して新規 Authenticator や Credential を取得することになる場合もある.
場合によっては CSP が有効期限切れから一定期間は再発行リクエストを受け入れることもある.

<!-- As noted above, CSPs maintain status information about credentials they issue. CSPs will generally assign a finite lifetime when issuing credentials to limit the maintenance period. When the status changes, or when the credentials near expiration, credentials may be renewed or re-issued; or, the credential may be revoked and/or destroyed. Typically, the subscriber authenticates to the CSP using his or her existing, unexpired authenticator and credential in order to request issuance of a new authenticator and credential. If the subscriber fails to request authenticator and credential re-issuance prior to their expiration or revocation, he or she may be required to repeat the enrollment process to obtain a new authenticator and credential. Alternatively, the CSP may choose to accept a request during a grace period after expiration. -->

<a name="Figure1"></a>
<div class="text-center" markdown="1">
![](sp800-63-3/media/model.png)

**Figure 1 - Digital Authentication Model**
</div>

### 4.2. Enrollment and Identity Proofing

基準となる要件は [Special Publication 800-63A, Enrollment and Identity Proofing](sp800-63a.html) を参照のこと.

<!-- Normative requirements can be found in [Special Publication 800-63A, Enrollment and Identity Proofing](sp800-63a.html). -->

前セクションでは Digital Authentication Model に登場する複数の主体が登場した.
本セクションでは, それら各主体のうち, 登録および Identity Proofing に関与する主体間の関連や責任分担について詳細にまとめる.

<!-- The previous section introduced the different participants in the conceptual digital authentication model. This section provides additional details regarding the relationships and responsibilities of the participants involved with enrollment and identity proofing. -->

個人はこのステージでは Applicant と呼ばれ, CSP に対して Credential 発行を要求する.
Applicant が Identity Proofing に成功すると, CSP は Authenticator を発行し, 当該個人は CSP の Subscriber となる.

<!-- An individual, referred to as an applicant at this stage, requests credentials from a CSP. If the applicant is successfully proofed and authenticators are issued by a CSP, the individual is then termed a subscriber of that CSP. -->

CSP は各 Subscriber をユニークに識別するメカニズムを確立し, Subscriber の Credential を登録し, Subscriber に発行された Authenticator を監視する.
Subscriber が登録時に Authenticator を受け取ることもあれば, Subscriber がすでに所有している Authenticator を CSP が紐付けることもあり, あとで必要になった段階で Authenticator を生成することもある.
Subscriber は自身の Authenticator を管理し, CSP に対する自身の責任を果たす義務を負う.
CSP は各 Subscriber の登録レコードを管理し, リカバリなどに対応する.

<!-- The CSP establishes a mechanism to uniquely identify each subscriber, register the subscriber’s credentials, and track the authenticators issued to that subscriber. The subscriber may be given authenticators at the time of enrollment, the CSP may bind authenticators the subscriber already has, or they may be generated later as needed. Subscribers have a duty to maintain control of their authenticators and comply with their responsibilities to the CSP. The CSP maintains enrollment records for each subscriber to allow recovery of enrollment records. -->

### 4.3. Authentication and Lifecycle Management

基準となる要件は [Special Publication 800-63B, Authentication and Lifecycle Management](sp800-63b.ja.html) を参照のこと.

#### 4.3.1. Authenticators

The classic paradigm for authentication systems identifies three factors as the cornerstone of authentication:  

* Something you know (for example, a password)
* Something you have (for example, an ID badge or a cryptographic key)
* Something you are (for example, a fingerprint or other biometric data)

Multi-factor authentication refers to the use of more than one of the factors listed above. The strength of authentication systems is largely determined by the number of factors incorporated by the system. Implementations that use two different factors are considered to be stronger than those that use only one factor; systems that incorporate all three factors are stronger than systems that only incorporate two of the factors. As discussed in [Section 4.1](#4-1), other types of information, such as location data or device identity, may be used by an RP or verifier to evaluate the risk in a claimed identity, but they are not considered authentication factors.

In digital authentication the claimant possesses and controls one or more authenticators that have been registered with the CSP and are used to prove the claimant’s identity. The authenticator(s) contains secrets the claimant can use to prove that he or she is a valid subscriber, the claimant authenticates to a system or application over a network by proving that he or she has possession and control of a authenticator.

The secrets contained in authenticators are based on either public key pairs (asymmetric keys) or shared secrets (symmetric keys). A public key and a related private key comprise a public key pair. The private key is stored on the authenticator and is used by the claimant to prove possession and control of the authenticator. A verifier, knowing the claimant’s public key through some credential (typically a public key certificate), can use an authentication protocol to verify the claimant’s identity, by proving that the claimant has possession and control of the associated private key authenticator.

Shared secrets stored on authenticators may be either symmetric keys or passwords (as opposed to the asymmetric secrets described above, which subscribers need not share with the authenticator). While both keys and passwords can be used in similar protocols, one important difference between the two is how they relate to the subscriber. While symmetric keys are generally stored in hardware or software that the subscriber controls, passwords are intended to be memorized by the subscriber. As such, a key is a secret stored on behalf of the subscriber, whereas subscribers are expected to store passwords within their mind. Since most users choose short passwords to facilitate memorization and ease of entry, passwords typically have fewer characters than cryptographic keys. Further, whereas systems choose keys at random, users attempting to choose memorable passwords will often select from a very small subset of the possible passwords of a given length, and many will choose very similar values. As such, whereas cryptographic keys are typically long enough to make network-based guessing attacks untenable, user-chosen passwords may be vulnerable—especially if no defenses are in place.

In this document, authenticators always contain a secret. Some of the classic authentication factors do not apply directly to digital authentication. For example, an ID badge is something you have, and is useful when authenticating to a human (e.g., a guard), but is not a authenticator for digital authentication. Authentication factors classified as something you know are not necessarily secrets, either. Knowledge based authentication, where the claimant is prompted to answer questions that can be confirmed from public databases, also does not constitute an acceptable secret for digital authentication. More generally, something you are does not generally constitute a secret. Accordingly, this recommendation does not permit the use of biometrics as a authenticator.

However, this recommendation does accept that authentication systems that incorporate all three factors offer better security than systems that only incorporate two of the factors. A digital authentication system may incorporate multiple factors in either of two ways. The system may be implemented so that multiple factors are presented to the verifier, or some factors may be used to protect a secret that will be presented to the verifier. If multiple factors are presented to the verifier, each will need to be a authenticator (and therefore contain a secret). If a single factor is presented to the verifier, the additional factors are used to protect the authenticator and need not themselves be authenticators.

For example, consider a piece of hardware (the authenticator) that contains a cryptographic key (the authenticator secret) where access is protected with a fingerprint. When used with the biometric, the cryptographic key produces an output that is used in the authentication process to authenticate the claimant. An impostor must steal the encrypted key (by stealing the hardware) and replicate the fingerprint to use the authenticator. This specification considers such a device to effectively provide two factor authentication, although the actual authentication protocol between the verifier and the claimant simply proves possession of the key.

As noted above, biometrics, when employed as a single factor of authentication, do not constitute acceptable secrets for digital authentication, but they do have their place in this specification. Biometric characteristics are unique personal attributes that can be used to verify the identity of a person who is physically present at the point of verification. They include facial features, fingerprints, iris patterns, voiceprints, and many other characteristics. [Special Publication 800-63A, Enrollment and Identity Proofing](sp800-63a.html) recommends that biometrics be used in the enrollment process for higher levels of assurance to later help prevent a subscriber who is registered from repudiating the enrollment, to help identify those who commit enrollment fraud, and to unlock authenticators.

#### 4.3.2. Credentials

As described in the preceding sections, credentials bind an authenticator to the subscriber as part of the issuance process. Credentials are stored and maintained by the CSP. The claimant possesses a authenticator, but is not necessarily in possession of the electronic credentials. For example, database entries containing the user attributes are considered to be credentials for the purpose of this document but are possessed by the verifier. X.509 public key certificates are a classic example of credentials the claimant can (and often does) possess.

#### 4.3.3. Authentication Process

The authentication process begins with the claimant demonstrating to the verifier possession and control of a authenticator that is bound to the asserted identity through an authentication protocol. Once possession and control has been demonstrated, the verifier verifies that the credential remains valid, usually by interacting with the CSP.

The exact nature of the interaction between the verifier and the claimant during the authentication protocol is extremely important in determining the overall security of the system. Well-designed protocols can protect the integrity and confidentiality of traffic between the claimant and the verifier both during and after the authentication exchange, and it can help limit the damage that can be done by an attacker masquerading as a legitimate verifier.

Additionally, mechanisms located at the verifier can mitigate online guessing attacks against lower entropy secrets like passwords and PINs by limiting the rate at which an attacker can make authentication attempts or otherwise delaying incorrect attempts. Generally, this is done by keeping track of and limiting the number of unsuccessful attempts, since the premise of an online guessing attack is that most attempts will fail.

The verifier is a functional role, but is frequently implemented in combination with the CSP and/or the RP. If the verifier is a separate entity from the CSP, it is often desirable to ensure that the verifier does not learn the subscriber’s authenticator secret in the process of authentication, or at least to ensure that the verifier does not have unrestricted access to secrets stored by the CSP.

### 4.4. Federation and Assertions

Normative requirements can be found in [Special Publication 800-63C, Federation and Assertions](sp800-63c.html).

Overall, SP 800-63-3 does not presuppose a federated identity architecture; rather, the guidance is agnostic to the types of models that exist in the marketplace, allowing agencies to deploy a digital authentication scheme according to their own requirements. However, identity federation, consistent with the National Strategy for Trusted Identities in Cyberspace (NSTIC) [[NSTIC]](#theNSTIC), is preferred over a number of siloed identity systems that each serve a single agency or RP.

Federated architectures have many significant benefits, including, but not limited to:  

* Enhanced user experience.  For example, an individual can be identity proofed once and can reuse the issued credential at multiple RPs
* Cost reduction, to both the user (one authenticator) and the agency (reduction in IT infrastructure)
* Data minimization: agencies do not need to pay for collection, storage, disposal, and compliance activities related to storing personal information
* Privacy enhancing
* Pseudonymous attribute assertions. Agencies can request a minimized set of attributes, to include claims, to fulfill service delivery.
* Mission enablement. Agencies can focus on mission, rather than the business of identity management.

The following sections discuss the components of a federated identity architecture should an agency elect this type of model.

#### 4.4.1 Assertions

Upon completion of the authentication process, the verifier generates an assertion containing the result of the authentication and provides it to the RP. If the verifier is implemented in combination with the RP, the assertion is implicit. If the verifier is a separate entity from the RP, as in typical federated identity models, the assertion is used to communicate the result of the authentication process, and optionally information about the subscriber, from the verifier to the RP. Assertions may be communicated directly to the RP, or can be forwarded through the subscriber, which has further implications for system design.

An RP trusts an assertion based on the source, the time of creation, and the corresponding trust framework that governs the policies and process of CSPs and RPs. The verifier is responsible for providing a mechanism by which the integrity of the assertion can be confirmed.

The RP is responsible for authenticating the source (the verifier) and for confirming the integrity of the assertion. When the verifier passes the assertion through the subscriber, the verifier must protect the integrity of the assertion in such a way that it cannot be modified by the subscriber. However, if the verifier and the RP communicate directly, a protected session may be used to provide the integrity protection. When sending assertions across an open network, the verifier is responsible for ensuring that any sensitive subscriber information contained in the assertion can only be extracted by an RP that it trusts to maintain the information’s confidentiality.

Examples of assertions include:

* SAML Assertions – SAML assertions are specified using a mark-up language intended for describing security assertions. They can be used by a verifier to make a statement to an RP about the identity of a claimant. SAML assertions may optionally be digitally signed.
* OpenID Connect Claims - OpenID Connect are specified using JavaScript Object Notation (JSON) for describing security, and optionally, user claims.  JSON user info claims may optionally be digitally signed.
* Kerberos Tickets – Kerberos Tickets allow a ticket granting authority to issue session keys to two authenticated parties using symmetric key based encapsulation schemes.

#### 4.4.2. Relying Parties

An RP relies on results of an authentication protocol to establish confidence in the identity or attributes of a subscriber for the purpose of conducting an online transaction. RPs may use a subscriber’s authenticated identity (pseudonymous or non-pseudonymous), the IAL, AAL and/or FAL (federation assurance level, indicating the strength of the assertion protocol), and other factors to make access control or authorization decisions. The verifier and the RP may be the same entity, or they may be separate entities. If they are separate entities, the RP normally receives an assertion from the verifier. The RP ensures that the assertion came from a verifier trusted by the RP. The RP also processes any additional information in the assertion, such as personal attributes or expiration times.

### 4.5. Assurance Levels

The overall M-04-04 LOA is determined by combining the discrete assurance level for each of the components of the architecture. For instance, to achieve M-04-04 LOA3:

* The enrollment and identity proofing process would, at a minimum, use IAL 1 or 2 processes.
* The authenticator (or combination of authenticators) would have an AAL of 2 or higher.
* Authentication assertions (if used) would have an FAL of 2 or higher.

The overall level is determined by the lowest level because it will likely be the target of an attacker. For example, if a system uses an authenticator that has AAL 2 assurance, but uses assertion mechanisms at FAL 3, the attacker will likely focus on gaining access to the authenticator since it is easier to attack a system component meeting AAL 2 rather than attacking the assertion that meets FAL 3.
