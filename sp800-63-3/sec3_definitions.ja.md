<a name="sec3"></a>

## 3. Definitions and Abbreviations

Authentication 分野で使われる用語は幅広く, 多くの用語は SP 800-63 との整合性を保っているものの, いくつかは本リビジョンから定義が変更になっている.
多くの用語に複数の定義がありうるため, 本ドキュメントにおける定義を明確にする必要がある.

<!-- There is a wide variety of terms used in the area of authentication. While the definitions of many terms are consistent with the earlier versions of SP 800-63, some have changed in this revision. Since there is no single, consistent definition of many of these terms, careful attention to how the terms are defined here is warranted. -->

本セクションでは, 本ドキュメントで利用される用語の定義を行う.
SP 800-63 ドキュメント群のその他のドキュメントで利用される定義や略語は, それぞれのドキュメントにて定義する.

<!-- The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document family for additional definitions and abbreviations specific to their content. -->

#### Address of Record

許可された手段によって特定個人とのコミュニケーションに利用可能な, 有効かつ検証済の (物理的またはデジタルの) 場所情報.

<!-- The validated and verified location (physical or digital) where an individual can receive communications using approved mechanisms. -->

#### Applicant

登録および Identity Proofing のプロセスを受けている主体.

<!-- A party undergoing the processes of registration and identity proofing. -->

#### Assertion

Verifier から Relying Party (RP) に対して送られる, Subscriber の Identity 情報を含んだ Statement.
Assertion は検証済属性情報を含むこともある.

<!-- A statement from a verifier to a relying party (RP) that contains identity information about a subscriber. Assertions may also contain verified attributes. -->

#### Assurance

[[OMB M-04-04]](#M-04-04) および本ドキュメントのコンテキストにおいては, Assurance とは 1) 当該 Credential を発行された個人の Identity を確立する審査プロセスにおける確からしさの度合い, および 2) 当該 Credential の提示者が当該 Credential の発行対象の個人と同一であることの確からしさの度合い, の2つを持って定義される.

<!-- In the context of [[OMB M-04-04]](#M-04-04) and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of an individual to whom the credential was issued, and 2) the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued. -->

#### Asymmetric Keys

公開鍵と秘密鍵からなる鍵ペア.
暗号化と復号, 署名生成と署名検証など, 対となるオペレーションに用いられる.

<!-- Two related keys, a public key and a private key that are used to perform complementary operations, such as encryption and decryption or signature generation and signature verification. -->

#### Attack

認可を持たない個人が, Verifier や Relying Party をだまして当該個人を Subscriber だと信じ込ませようとする行為.

<!-- An attempt by an unauthorized individual to fool a verifier or a relying party into believing that the unauthorized individual in question is the subscriber. -->

#### Attacker

不正な意図を持ち情報システムに不正アクセスする主体.

<!-- A party who acts with malicious intent to compromise an information system. -->

#### Attribute

人や物に関する生来の性質や特徴. (詳しくは [\[ICAM\]](#ICAM) を参照のこと)

<!-- A claim of a named quality or characteristic inherent in or ascribed to someone or something. (See term in [\[ICAM\]](#ICAM) for more information.) -->

#### Authentication

ユーザーや情報システム自体の Identity の確からしさを確立するプロセス.

<!-- The process of establishing confidence in the identity of users or information systems. -->

#### Authentication Protocol

Claimant が, 正規の Authenticator の所有および管理権限を示すことで自身の Identity を確立するプロセスにおいて, Claimant と Verifier の間でやりとりされる一連のメッセージの定義.
Claimant が意図した Verifier とコミュニケーションしていることを立証するためのプロセスを含むこともある.

<!-- A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of a valid authenticator to establish his/her identity, and optionally, demonstrates to the claimant that he or she is communicating with the intended verifier. -->

#### Authentication Secret

あらゆる鍵を示す一般的な呼び名.
Authentication Protocol において Attacker が Subscriber になりすますために利用することもできる.

<!-- A generic term for any secret value that could be used by an attacker to impersonate the subscriber in an authentication protocol. -->

Authentication Secret は *short-term authentication secrets* と *long-term authentication secrets* に分類することができ, 前者は限定的な期間のみ利用可能なもの, 後者は手動でリセットされるまで使い続けられるものを示す.
Authenticator Secret は long-term authentication secret の代表的な例であり, Authenticator の出力する鍵が Authenticator Secret と異なる場合, その出力された鍵は一般的に short-term authentication secret である.

<!-- These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The authenticator secret is the canonical example of a long term authentication secret, while the authenticator output, if it is different from the authenticator secret, is usually a short term authentication secret. -->

#### Authenticator

Claimant が所有および管理するもので, 典型的な例としては暗号モジュールやパスワード等がある.
Authenticator は Claimant の Identity を認証するために用いられる.
本ガイドラインの前リビジョンにおいて *token* と呼ばれていたものと同等である.

<!-- Something that the claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant’s identity. In previous versions of this guideline, this was referred to as a *token*. -->

#### Authenticator Assurance Level (AAL)

Claimant が Subscriber の Authenticator を管理していることを証明する Authentication プロセスの頑健性を示す指標.

<!-- A metric describing robustness of the authentication process proving that the claimant is in control of a given subscriber's authenticator(s). -->

#### Authenticator Secret

Authenticator に内含される鍵.

<!-- The secret value contained within an authenticator. -->

#### Authenticity

データが意図された情報源から得られたものであるという性質.

<!-- The property that data originated from its purported source. -->

#### Biometrics

個人の行動や生体情報をもとに個人を自動認証すること.

<!-- Automated recognition of individuals based on their behavioral and biological characteristics. -->

本ドキュメントでは, Biometrics は Authenticator のアンロックや登録の否認防止目的で用いられることもある.

<!-- In this document, biometrics may be used to unlock authenticators and prevent repudiation of registration. -->

#### Claimant

Authentication Protocol により Identity を検証される主体.

<!-- A party whose identity is to be verified using an authentication protocol. -->

#### Claimed Identity

Applicant により申告された現在の Personal Name, 誕生日, 住所. ([[GPG45]](#gpg45))

<!-- A declaration by the applicant of their current Personal Name, date of birth and address. [[GPG45]](#gpg45) -->

#### Credential

ある Identity (および付加的属性) を Subscriber が所有ないしは管理する Authenticator に紐付ける信頼の置けるオブジェクトもしくはデータ構造.

<!-- An object or data structure that authoritatively binds an identity (and optionally, additional attributes) to an authenticator possessed and controlled by a subscriber. -->

一般的に Credential は Subscriber に管理されることが想定されるが, 本ドキュメントでは Subscriber の Authenticator と Identity の紐付けを確立する CSP 管理下の電子レコードを指すこともある.

<!-- While common usage often assumes that the credential is maintained by the subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the subscriber’s authenticator(s) and identity. -->

#### Credential Service Provider (CSP)

Subscriber の Authenticator を発行もしくは登録し, Subscriber に電子的な Credential を発行する信頼された主体.
CSP は自身が運営する Registration Authorities (RAs) および Verifier を内包することもある.
CSP は独立した第三者となることもあれば, 自身で発行した Credential を用いて自らサービスを提供することもある.

<!-- A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. The CSP may encompass Registration Authorities (RAs) and verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use. -->

#### Cryptographic Key

復号, 暗号化, 署名生成, 署名検証等の暗号論的オペレーションを管理するために用いられる値.
本ドキュメントでは, NIST SP 800-57 Part 1 の Table 2 で述べられた最低限の要件を満たすものとする.

<!-- A value used to control cryptographic operations, such as decryption, encryption, signature generation or signature verification. For the purposes of this document, key requirements shall meet the minimum requirements stated in Table 2 of NIST SP 800-57 Part 1. -->

Asymmetric keys および Symmetric key も参照のこと.

<!-- See also Asymmetric keys, Symmetric key. -->

#### Cryptographic Authenticator

Cryptographic Key を利用する Authenticator.

<!-- An authenticator where the secret is a cryptographic key. -->

#### Digital Authentication

情報システムに対して, デジタル表現されたユーザーの Identity の確からしさを確立するプロセス.

<!-- The process of establishing confidence in user identities digitally presented to an information system. -->

#### Digital Signature

秘密鍵を用いてデータに電子署名を行い, 公開鍵を用いて署名検証を行う, Asymmetric Key を用いたオペレーション.
Digital Signature は Authenticity Protection (真正性), Integrity Protection (完全性), Non-Repudication (否認防止) を提供する.

<!-- An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation. -->

#### Federal Information Security Management Act (FISMA)

E-Government Act の Title III に規定されている.
FISMA は, 各政府機関に対して, 当該機関のオペレーションおよびアセットを支える情報および情報システムにおける情報セキュリティを確保する機関全体を通したプログラムの開発, 記録, 実装を要求する.
ここで保護対象となる情報および情報システムには, 他の機関や受託業者などに提供および管理されるものも含む.

<!-- Title III of the E-Government Act requiring each federal agency to develop, document, and implement an agency-wide program to provide information security for the information and information systems that support the operations and assets of the agency, including those provided or managed by another agency, contractor, or other source. -->

#### Federal Information Processing Standard (FIPS)

Information Technology Management Reform Act (Public Law 104-106) のもとで, Secretary of Commerce は National Institute of Standards and Technology (NIST) が連邦のコンピューターシステムのために作成した標準およびガイドラインを承認する.
これらの標準およびガイドラインは, NIST によって Federal Information Processing Standards (FIPS) として発行され, 政府全体で利用される.
NIST は, 連邦政府がセキュリティや相互運用性に対する必要性を持っており, 利用可能な業界標準やソリューションが存在しない場合に, FISP を作成する.

<!-- Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves standards and guidelines that are developed by the National Institute of Standards and Technology (NIST) for Federal computer systems. These standards and guidelines are issued by NIST as Federal Information Processing Standards (FIPS) for use government-wide. NIST develops FIPS when there are compelling Federal government requirements such as for security and interoperability and there are no acceptable industry standards or solutions. See background information for more details. -->

FISP ドキュメントは FISP ホームページからオンラインで閲覧可能である. : <http://www.nist.gov/itl/fips.cfm>

<!-- FIPS documents are available online through the FIPS home page: <http://www.nist.gov/itl/fips.cfm> -->

#### Federation

一連のネットワークシステム間で Identity および認証情報の伝搬を行うためのプロセス.

<!-- A process that allows for the conveyance of identity and authentication information across a set of networked systems. -->

#### Identity

特定のコンテキストにおいてある人物を他と区別できるかたちで表現する属性の集合.

<!-- A set of attributes that uniquely describe a person within a given context. -->

#### Identity Assurance Level (IAL)

Applicant の Claimed Identity が本人の本物の Identity であることの確からしさの度合いをあらわす指標.

<!-- A metric describing degree of confidence that the applicant’s claimed identity is their real identity. -->

#### Identity Proofing

CSP および Registration Authority (RA) が, Credential 発行のためにある人物に関する情報を収集および検証するプロセス.

<!-- The process by which a CSP and a Registration Authority (RA) collect and verify information about a person for the purpose of issuing credentials to that person. -->

#### Multi-Factor

2つ以上の Authentication Factor を用いる認証システムや Authenticator の特徴.

<!-- A characteristic of an authentication system or an authenticator that uses more than one authentication factor. -->

Authentication Factor としては, Something You Know, Something You Have, Something You Are の3種類がある.

<!-- The three types of authentication factors are something you know, something you have, and something you are. -->

#### Network

オープンなコミュニケーションの伝達手段.
Internet がその代表例である.
Network は Claimant とその他の主体の間でメッセージを伝達するために用いられる.
特に明示されない限り, Network のセキュリティは前提とされず, オープンであり, 任意の主体 (Claimant, Verifier, CSP および RP) 間の任意の点において自発的な攻撃 (なりすまし, Man-in-the-Middle, Session Hijacking 等) や受動的な攻撃 (盗聴等) にさらされうるものと想定される.

<!-- An open communications medium, typically the Internet, that is used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (i.e., impersonation, man-in-the-middle, session hijacking) and passive (i.e., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP or RP). -->

#### Password

Claimant が記憶し自身の Identity の認証に用いる鍵.
Password は一般的に文字列である.

<!-- A secret that a claimant memorizes and uses to authenticate his or her identity. Passwords are typically character strings. -->

#### Personal Identification Number (PIN)

10進数の数値のみで構成された Password.

<!-- A password consisting only of decimal digits. -->

#### Personally Identifiable Information (PII)

OMB Circular A-130 で定義されているように, Personally Identifiable Information とは個人の Identity を識別したり追跡するために用いられる情報である.
単体の情報で個人を識別・追跡可能なものもあれば, 特定の個人に紐付け済もしくは紐付け可能なその他の情報と組み合わせることで識別・追跡可能となるものもある.

<!-- As defined by OMB Circular A-130, Personally Identifiable Information means information that can be used to distinguish or trace an individual's identity, either alone or when combined with other information that is linked or linkable to a specific individual. -->

#### Private Key

Asymmetric Key ペアの秘密鍵.
データへの署名生成や復号に用いられる.

<!-- The secret part of an asymmetric key pair that is used to digitally sign or decrypt data. -->

#### Pseudonymous Identifer

RP による Subscriber の推測を許さず, かつ RP が複数のインタラクションに渡って Subscriber の Claimed Identity を紐づけられるような, 意味のないユニークな識別子.

<!-- A meaningless, but unique number that does not allow the RP to infer the subscriber but which does permit the RP to associate multiple interactions with the subscriber’s claimed identity. -->

#### Public Key

Asymmetric Key ペアの公開鍵.
データへの署名検証や暗号化に用いられる.

<!-- The public part of an asymmetric key pair that is used to verify signatures or encrypt data. -->

#### Public Key Certificate

Certificate Authority によって発行され, Certificate Authority の秘密鍵でデジタル署名された電子文書.
Public Key Certificate により Subscriber の名前が Public Key と紐づけられる.
当該 Certificate により識別される Subscriber のみが Private Key の管理およびアクセス権限を持っていることが暗示される.
[[RFC 5280]](#RFC5280) も参照のこと.

<!-- A digital document issued and digitally signed by the private key of a Certificate authority that binds the name of a subscriber to a public key. The certificate indicates that the subscriber identified in the certificate has sole control and access to the private key. See also [[RFC 5280]](#RFC5280). -->

#### Public Key Infrastructure (PKI)

Certificate と Public-Private Key Pair を管理する目的で利用される, 一連のポリシー, プロセス, サーバープラットフォーム, ソフトウェア, ワークステーションなど.
Public Key Certificate の発行, 管理, 失効を行う能力を備える.

<!-- A set of policies, processes, server platforms, software and workstations used for the purpose of administering certificates and public-private key pairs, including the ability to issue, maintain, and revoke public key certificates. -->

#### Registration

Applicant が CSP の Subscriber となるべく申請し, RA が CSP に代わって Applicant の Identity を確認する一連のプロセス.

<!-- The process through which an applicant applies to become a subscriber of a CSP and an RA validates the identity of the applicant on behalf of the CSP. -->

#### Registration Authority (RA)

CSP に対して Subscriber の Identity および Attribute を発行および保証する信頼された主体.
RA は, CSP の一部であることもあれば, CSP から独立した主体であることもあるが, CSP と何らかの結び付きを持つ.

<!-- A trusted entity that establishes and vouches for the identity or attributes of a subscriber to a CSP. The RA may be an integral part of a CSP, or it may be independent of a CSP, but it has a relationship to the CSP(s). -->

#### Relying Party (RP)

Subscriber の Authenticator および Credential, Verifier の Claimant Identity に関する Assertion を信頼して, トランザクションを処理したり情報やシステムへのアクセスを許可したりする主体.

<!-- An entity that relies upon the subscriber's authenticator(s) and credentials or a verifier's assertion of a claimant’s identity, typically to process a transaction or grant access to information or a system. -->

#### Remote

(*Remote Authentication や Remote Transaction といったコンテキストで*) 単一組織によるセキュリティ対策のみでは End-to-End での確実な保護が期待できないような状況下での, ネットワーク接続されたデバイス間の情報交換.

<!-- (*As in remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization’s security controls. -->

注) Internet を介した情報交換はすべて Remote とみなされる.

<!-- Note: Any information exchange across the Internet is considered remote. -->

#### Risk Assessment

システムセキュリティに対するリスクを特定した上で, その発生確率やもたらされる影響を判定し, その影響を軽減する追加の保護策を決定していくプロセス.
Risk Assessment は Risk Management の一部であり, Risk Analysis と同義である.

<!-- The process of identifying the risks to system security and determining the probability of occurrence, the resulting impact, and additional safeguards that would mitigate this impact. Part of Risk Management and synonymous with Risk Analysis. -->

#### Shared Secret

Claimant と Verifier が知っている, Authentication で使われる鍵.

<!-- A secret used in authentication that is known to the claimant and the verifier. -->

#### Special Publication (SP)

NIST が発行する出版物の一形態.
特に Special Publication 800 シリーズは, Information Technology Laboratory による研究活動, ガイドライン, コンピュターセキュリティ分野における公共福祉のための支援活動, 民間・政府・学術組織との協調的な活動などに関するレポートとなっている.

<!-- A type of publication issued by NIST. Specifically, the Special Publication 800-series reports on the Information Technology Laboratory's research, guidelines, and outreach efforts in computer security, and its collaborative activities with industry, government, and academic organizations. -->

#### Subscriber

CSP から Credential や Authenticator を受け取る主体.

<!-- A party who has received a credential or authenticator from a CSP. -->

#### Symmetric Key

暗号化と復号, メッセージ認証コードの生成と検証などの, 対となる暗号論的オペレーションの両方で用いられる暗号論的な鍵.

<!-- A cryptographic key that is used to perform both the cryptographic operation and its inverse, for example to encrypt and decrypt, or create a message authentication code and to verify the code. -->

#### Token

*Authenticator* の定義を参照のこと.

<!-- See *Authenticator*. -->

#### Unverified Name

Identity Proofing により検証されていない Subscriber の名前.

<!-- A subscriber name that is not verified as meaningful by identity proofing. -->

#### Valid

ある ID (身分証明書) について, それが期限切れや失効していないこと.

<!-- In reference to an ID, the quality of not being expired or revoked. -->

#### Verified Name

Identity Proofing により検証された Subscriber の名前.

<!-- A subscriber name that has been verified by identity proofing. -->

#### Verifier

Claimant の Identity を検証する主体.
Claimant Identity の検証は, Authentication Protocol により Claimant が1つ以上の Authenticator を所持・管理していることを検証することで行われる.
Verifier は Authenticator と Identity を紐付ける Credential を確認し, それらの状態を確認する必要があることもある.

<!-- An entity that verifies the claimant’s identity by verifying the claimant’s possession and control of one or two authenticators using an authentication protocol. To do this, the verifier may also need to validate credentials that link the authenticator(s) and identity and check their status. -->
