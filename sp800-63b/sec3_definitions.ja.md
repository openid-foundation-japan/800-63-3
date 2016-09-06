<a name="sec3"></a>

<!-- ## 3. Definitions and Abbreviations -->

## 3. 定義及び略語

<!-- There is a variety of terms used in the area of authentication. While the definitions of many terms are consistent with the original version of SP 800-63, some have changed in this revision. Since there is no single, consistent definition of many of these terms, careful attention to how the terms are defined here is warranted. -->

認証分野では様々な用語が用いられる。多くの用語はSP 800-63の初版のものと一貫性があるものの、この版で変更になっているものがいくつかある。そのため、複数の定義の一貫性をとるため、本章で定義される用語がどのような内容であると宣言されているか注意すること。

<!-- The definitions in this section are primarily those that are referenced in this document. Refer to the other documents in the SP 800-63 document family for additional definitions and abbreviations specific to their content. -->

本章の定義は本章で参照するものである。SP 800-63の他の構成文章における追加の定義及び用語の詳細は、それぞれの文書の内容を参照すること。

<!-- #### Active Attack -->

#### 能動的攻撃 (Active Attack)
<!-- An attack on the authentication protocol where the attacker transmits data to the claimant, Credential Service Provider, verifier, or Relying Party. Examples of active attacks include man-in-the-middle, impersonation, and session hijacking. -->
攻撃者が認証の要求者、クレデンシャルサービスプロバイダ、検証器、リライングパーティに対してデータを送信するような認証プロトコルにおける攻撃のこと。能動的攻撃の例として、中間者攻撃、なりすまし、セッションハイジャックが挙げられる。

<!--#### Approved-->

#### 承認済み (Approved)
<!-- Federal Information Processing Standard (FIPS) approved or NIST recommended. An algorithm or technique that is either 1) specified in a FIPS or NIST Recommendation, or 2) adopted in a FIPS or NIST Recommendation. -->
連邦情報処理標準(FIPS)により承認されている、またはNISTにより推奨されていること。アルゴリズムや技術が 1) FIPSまたはNIST推奨で指定されたものであること。または 2) FIPSまたはNIST推奨に適合していること

<!--#### Assertion-->

#### アサーション (Assertion)
<!--A statement from a verifier to a Relying Party (RP) that contains identity information about a subscriber. Assertions may also contain verified attributes.-->
検証者からリライングパーティー(RP)に対する文書であり、加入者に関するアイデンティティ情報を含む。アサーションは妥当性が検証されている属性を含んでもよい。

<!-- #### Assertion Reference -->

#### アサーションリファレンス (Assertion Reference)
<!--
A data object, created in conjunction with an assertion, which identifies the verifier and includes a pointer to the full assertion held by the verifier. -->
アサーションと関連づけられて作成されたデータオブジェクト。検証者を識別するとともに、検証者が取り扱う完全なアサーションへのポインタを含んでいる。

<!--#### Assurance-->

#### 確実性 (Assurance)
<!-- In the context of [[OMB M-04-04]](#M-04-04) and this document, assurance is defined as 1) the degree of confidence in the vetting process used to establish the identity of an individual to whom the credential was issued, and 2) the degree of confidence that the individual who uses the credential is the individual to whom the credential was issued. -->

[[OMB M-04-04]](#M-04-04)及び本書の中で、確実性の定義は、1) クレデンシャルが発行されている個人のアイデンティティを証明するため審査プロセスの信頼度、及び 2) クレデンシャルを利用している個人が、そのクレデンシャルが発行されている個人に一致することの信頼度、と定義される。

<!--#### Asymmetric Keys-->

#### 非対称鍵 (Asymmetric Keys)
<!--Two related keys, a public key and a private key that are used to perform complementary operations, such as encryption and decryption or signature generation and signature verification.-->

2つの関連する鍵で、暗号化と複合、署名生成と署名検証といった相補的な操作を行うことができる公開鍵と秘密鍵のこと。


<!--#### Attack-->

#### 攻撃 (Attack)
<!--An attempt by an unauthorized individual to defeat security controls. For example, to fool a verifier or a Relying Party into believing that the unauthorized individual in question is the subscriber.-->

権限のない個人による、セキュリティ制限を突破する試み。例えば、検証者やリライングパーティを偽って、権限のない当該個人が加入者であると信じ込ませること。

<!--#### Attacker-->

#### 攻撃者 (Attacker)
<!--A party who acts with malicious intent to compromise an information system.-->

悪意をもって情報システムを侵害しようとする者。

<!--#### Attribute-->

#### 属性 (Attribute)
<!--A claim of a named quality or characteristic inherent in or ascribed to someone or something. (See term in [[ICAM]](#ICAM) for more information.)-->

何らかの人や物に固有または元来有する特徴や、指定の性質の申告。(詳細は[[ICAM]](#ICAM)の単語を参照)

<!--TODO-->

<!-- #### Authenticated Protected Channel-->

#### 認証済み保護チャネル (Authenticated Protected Channel)

<!--A communication channel that uses approved encryption where the initiator of the connection (client) has authenticated the recipient (server). Authenticated protected channels provide confidentiality and man-in-the-middle protection and are frequently used in the user authentication process. TLS [[BCP 195]](#bcp195) is an example of an authenticated protected channel when the certificate presented by the recipient is verified by the initiator.-->

接続の開始者(クライアント)が受信者(server)を予め認証しているような、承認済みの暗号化を利用する通信チャネル。認証済み保護チャネルは、機密性と中間者攻撃保護を提供し、ユーザ認証プロセスにおいて頻繁に利用される。TLS [[BCP 195]](#bcp195)は、認証済み保護チャネルの例の1つで、受信者が提示した証明書を開始者が検証することで実現される。

<!--#### Authentication-->

#### 認証 (Authentication)

<!--The process of establishing confidence in the identity of users or information systems.-->
ユーザや情報システムのアイデンティティが確かなものであることをを証明するプロセス。

<!--#### Authentication Protocol-->

#### 認証プロトコル (Authentication Protocol)
<!--A defined sequence of messages between a claimant and a verifier that demonstrates that the claimant has possession and control of a valid authenticator to establish his/her identity. Secure authentication protocols also demonstrate to the claimant that he or she is communicating with the intended verifier.-->

要求者と検証者との間でやり取りされるメッセージのシーケンスを定義したもので、要求者は、彼・彼女のアイデンティティを証明するための妥当な認証器を所有し、管理することを明らかにする。セキュアな認証プロトコルは、要求者に対し、彼・彼女が意図した検証者と通信をしているということを証明する。

<!--#### Authentication Protocol Run-->

#### 認証プロトコル実行 (Authentication Protocol Run)
<!--An exchange of messages between a claimant and a verifier that results in authentication (or authentication failure) between the two parties.-->

要求者と検証者との間でメッセージを交換し、2者間で認証(または認証失敗)結果を得ること。


<!--#### Authentication Secret-->

#### 認証シークレット (Authentication Secret)
<!--A generic term for any secret value that could be used by an attacker to impersonate the subscriber in an authentication protocol.-->
攻撃者が加入者を詐称するために利用できる可能性がある、任意のシークレット値に対する一般的な表現。

<!--These are further divided into *short-term authentication secrets*, which are only useful to an attacker for a limited period of time, and *long-term authentication secrets*, which allow an attacker to impersonate the subscriber until they are manually reset. The authenticator secret is the canonical example of a long term authentication secret, while the authenticator output, if it is different from the authenticator secret, is usually a short term authentication secret.-->

これらは更に 攻撃者が限られた期間しか利用することができない*短期間の認証シークレット*と、明示的にリセットされるまで攻撃者が加入者を詐称するために利用することができる*長期間の認証シークレット*に分類できる。認証器のシークレットは典型的な長期間の認証シークレットの例である。一方、認証器の出力は、その値が認証器のシークレットと異なるならば、通常、短期間の認証シークレットである。

<!--#### Authenticator-->

#### 認証器 (Authenticator)
<!--Something that the claimant possesses and controls (typically a cryptographic module or password) that is used to authenticate the claimant’s identity. In previous versions of this guideline, this was referred to as a *token*.-->

要求者が所有し、管理することができ、要求者のアイデンティティを認証するために利用することができるもの(典型的には暗号化モジュールやパスワード)。ガイドラインの以前の版では*トークン*とされていたものである。


<!--#### Authenticator Assurance Level (AAL)-->

#### 認証器保証レベル (AAL: Authenticator Assurance Level)

<!--A metric describing robustness of the authentication process proving that the claimant is in control of a given subscriber's authenticator(s).-->

要求者が指定された加入者の認証器を管理していることを証明する、認証プロセスの堅牢性を表す尺度。


<!--#### Authenticator Output-->

#### 認証器出力 (Authenticator Output)
<!--
The output value generated by an authenticator. The ability to generate valid authenticator outputs on demand proves that the claimant possesses and controls the authenticator. Protocol messages sent to the verifier are dependent upon the authenticator output, but they may or may not explicitly contain it.
-->
認証器によって生成される出力の値。必要な時に妥当な認証器出力を生成する能力は、要求者が認証器を所有し管理していることを証明する。検証者へ送信されるプロトコルメッセージは、認証器出力に依存するが、明示的に出力の値を含んでいるとは限らない。


<!--#### Authenticator Secret-->

#### 認証器シークレット (Authenticator Secret)
<!--
The secret value contained within an authenticator.
-->
認証器が保持するシークレット値。


<!--#### Bearer Assertion-->

#### 無記名アサーション (Bearer Assertion)
<!--
An assertion that does not provide a mechanism for the subscriber to prove that he or she is the rightful owner of the assertion. The RP has to assume that the assertion was issued to the subscriber who presents the assertion or the corresponding assertion reference to the RP.
-->
加入者が、自身がそのアサーションの正当な所有者であることを証明するメカニズムを提供しないアサーションのこと。
RPは、加入者がアサーションかRPやアサーションリファレンスを提示してきた場合、そのアサーションが加入者に対して発行されたものであると過程することになる。

<!--
#### Biometrics
-->

#### バイオメトリクス (Biometrics)
<!--
Automated recognition of individuals based on their behavioral and biological characteristics.
-->
個人の振る舞いや生物学的特徴にもとづいて自動的に認識すること。

<!--
In this document, biometrics may be used to unlock multifactor authenticators and prevent repudiation of registration.
-->
本書では、バイオメトリクスは他要素認証器のロック解除や、登録の否認防止で利用される。


<!--
#### Challenge-Response Protocol
-->

#### チャレンジ-レスポンス プロトコル (Challenge-Response Protocol)
<!--
An authentication protocol where the verifier sends the claimant a challenge (usually a random value or a nonce) that the claimant combines with a secret (such as by hashing the challenge and a shared secret together, or by applying a private key operation to the challenge) to generate a response that is sent to the verifier. The verifier can independently verify the response generated by the claimant (such as by re-computing the hash of the challenge and the shared secret and comparing to the response, or performing a public key operation on the response) and establish that the claimant possesses and controls the secret.
-->
検証者が要求者に対してチャレンジ(通常はランダム値やノンス)を送信し、要求者はシークレットと連結(チャレンジと共有シークレットを一緒にハッシュしたり、チャレンジに対して秘密鍵による操作を実施)して応答を生成し、検証者に返却するような認証プロトコルのこと。検証者は、要求者によって生成された応答を自身のみで検証（チャレンジと共有シークレットのハッシュを再計算してレスポンスと比較したり、レスポンスに対してい公開鍵による操作を実施）し、要求者がシークレットを所有し管理できることを証明することができる。

<!--
#### Claimant
-->

#### 要求者 (Claimant)
<!--
A party whose identity is to be verified using an authentication protocol.
-->
認証プロトコルを用いて自身のアイデンティティを検証する当事者。

<!--#### Completely Automated Public Turing test to tell Computers and Humans Apart (CAPTCHA)-->

#### キャプチャ (CAPTCHA: Completely Automated Public Turing test to tell Computers and Humans Apart)
<!--
An interactive feature added to web-forms to distinguish use of the form by humans as opposed to automated agents. Typically, it requires entering text corresponding to a distorted image or from a sound stream.
-->
Webフォームに利用者が人間と自動エージェントを区別するために追加する対話的な機能のこと。典型的には、その機能は、歪んだ画像や、音声に対応するテキストの入力を求める方式である。

<!--
#### Credential
-->

#### クレデンシャル (Credential)
<!--
An object or data structure that authoritatively binds an identity (and optionally, additional attributes) to an authenticator possessed and controlled by a subscriber.
-->
加入者によって所有、管理される認証器に対して、アイデンティティ（及びオプションで追加属性）を正式に関連付けるオブジェクトまたはデータ構造。

<!--
While common usage often assumes that the credential is maintained by the subscriber, this document also uses the term to refer to electronic records maintained by the CSP which establish a binding between the subscriber’s authenticator(s) and their identity.
-->
一般的な用途では、大抵はクレデンシャルは加入者によって維持管理されていると仮定するが、本書では、加入者の認証器と加入者のアイデンティティとの関連付けを確立するCSPによって維持管理される電子的記録について言及する用語として用いる。

<!--
#### Credential Service Provider (CSP)
-->

#### クレデンシャルサービスプロバイダ (CSP: Credential Service Provider)
<!--
A trusted entity that issues or registers subscriber authenticators and issues electronic credentials to subscribers. The CSP may encompass verifiers that it operates. A CSP may be an independent third party, or may issue credentials for its own use.
-->
加入者の認証器を発行・登録し、加入者に対して電子的なクレデンシャルを発行する、信頼されているエンティティ。CSPは自身が運用する検証者も包含しても良い。CSPは独立したサードパーティでも良く、自分自身で利用する目的でクレデンシャルを発行しても良い。


<!--
#### Cross Site Request Forgery (CSRF)
-->

#### クロスサイトリクエストフォージェリ (CSRF: Cross Site Request Forgery)
<!--
An attack in which a subscriber who is currently authenticated to an RP and connected through a secure session, browses to an attacker’s website which causes the subscriber to unknowingly invoke unwanted actions at the RP.
-->
RPに対して認証済みの加入者がセキュアなセッションを経由して接続している場合に発生する攻撃で、ブラウザで攻撃者のウェブサイトにアクセスすることで、加入者が意図せず望まないアクションをRPで実行してしまうもの。

<!--
For example, if a bank website is vulnerable to a CSRF attack, it may be possible for a subscriber to unintentionally authorize a large money transfer, merely by viewing a malicious link in a webmail message while a connection to the bank is open in another browser window.
-->

例えば、もし銀行のサイトがCSRFに対して脆弱である場合、単にユーザWebメールの本文中の悪意のあるリンクを参照するだけで、別のブラウザで銀行への接続が開かれ、加入者が意図せず大きな金額の資金移動を許可てしまう可能性がある。


<!--
#### Cross Site Scripting (XSS)
-->

#### クロスサイトスクリプティング (XSS: Cross Site Scripting)
<!--
A vulnerability that allows attackers to inject malicious code into an otherwise benign website. These scripts acquire the permissions of scripts generated by the target website and can therefore compromise the confidentiality and integrity of data transfers between the website and client. Websites are vulnerable if they display user supplied data from requests or forms without sanitizing the data so that it is not executable.
-->
攻撃者が、不正なコードを他の無害なページに対して注入することを許してしまう脆弱性。
これらのスクリプトはターゲットのウェブサイトで生成されるスクリプトの権限で動作し、ウェブサイトとクライアント間でのデータ転送の機密性や一貫性を侵害する。
ウェブサイトは、ユーザが入力するデータをリクエストやフォームから受け取り、サニタイズを施して実行不可能にすることなく表示してしまう場合に脆弱である。


<!--
#### Cryptographic Key
-->

#### 暗号鍵 (Cryptographic Key)
<!--
A value used to control cryptographic operations, such as decryption, encryption, signature generation or signature verification. For the purposes of this document, key requirements shall meet the minimum requirements stated in Table 2 of NIST SP 800-57 Part 1.
-->

複合、暗号、署名生成、署名検証といった暗号操作を制御するために利用される値。本書の目的において、鍵要求仕様はNIST SP 800-57 Part 1の表2で述べられている最小の要求仕様に一致させるものとする。

<!--
See also Asymmetric keys, Symmetric key.
-->
非対称鍵、対象鍵も合わせて参照のこと。

<!--#### Cryptographic Authenticator-->

#### 暗号認証器 (Cryptographic Authenticator)
<!--An authenticator where the secret is a cryptographic key.-->
シークレットが暗号鍵であるような認証器のこと。

<!--#### Data Integrity-->

#### データ一貫性 (Data Integrity)
<!--The property that data has not been altered by an unauthorized entity.-->
認可されていないエンティティによってデータが変更されることがない、という性質。

<!--#### Derived Credential-->

#### 派生クレデンシャル (Derived Credential)
過去に発行されたクレデンシャルと関連付けられている一つ以上の認証器の所有及び制御の証明に基づいて発行されるクレデンシャル。
したがって、アイデンティティの証明プロセスを重複して行うわけではない。

<!--
A credential issued based on proof of possession and control of one or more authenticators associated with a previously issued credential, so as not to duplicate the identity proofing process.
-->

<!--#### Digital Signature-->

#### デジタル署名 (Digital Signature)
プライベートキーを利用してデータに署名し、パブリックキーを利用して署名を検証する、非対称鍵の操作のこと。デジタル署名は真正性の保護、一貫性の保護、非否認性を実現する。

<!--
An asymmetric key operation where the private key is used to digitally sign data and the public key is used to verify the signature. Digital signatures provide authenticity protection, integrity protection, and non-repudiation.
-->

<!--#### Eavesdropping Attack-->

#### 盗聴攻撃 (Eavesdropping Attack)
認証プロトコルを受動的に聞き、情報を傍受する攻撃。傍受した情報は、後続の要求者に成りすました能動的攻撃で利用される。

<!--An attack in which an attacker listens passively to the authentication protocol to capture information which can be used in a subsequent active attack to masquerade as the claimant.-->

<!--#### Electronic Authentication (E-Authentication)-->

#### 電子的認証 (E-Authentication: Electronic Authentication)
情報システムに対して、電子的にユーザのアイデンティティの確かさを証明するプロセス。

<!--The process of establishing confidence in user identities electronically presented to an information system.-->


<!--#### Entropy-->

#### エントロピー (Entropy)
攻撃者がシークレットの値を決定することに対峙する際の不確実性の量の尺度。エントロピーは、通常ビットで表現される。

<!--A measure of the amount of uncertainty that an attacker faces to determine the value of a secret. Entropy is usually stated in bits.-->

<!--#### Equal Error Rate (EER)-->

#### 等価エラー率 (EER: Equal Error Rate)

センサーにおいて、マッチすべきものがマッチしない割合(False Match Rate: FMR)、及びマッチすべきではないものがマッチしてしまう割合(False Non-Match Rate: FNMR) が等しくなる地点の値である等価エラー率を、センサーの性能指数とする。等価エラー率が低ければ低いほど、センサーの検出結果がより確からしいものとなる。

<!--The value where the false match rate (FMR) and false non-match rate (FNMR) of a sensor are equal. EER is a figure of merit for the sensor; the lower the EER is, the more certain the sensor's decision is likely to be.-->

<!--#### Federal Information Security Management Act (FISMA)-->

#### Federal Information Security Management Act (FISMA)
Title III of the E-Government Actは各連邦政府機関に対し、運営や資源を支援する情報及び情報システムへの情報セキュリティを備えるための機関横断的なプログラムを、開発、記録、実行していくことを要求している。対象となる情報及び情報システムには、別の機関、業者や他の調達元によって導入・管理されるものも含まれる。

<!--Title III of the E-Government Act requiring each federal agency to develop, document, and implement an agency-wide program to provide information security for the information and information systems that support the operations and assets of the agency, including those provided or managed by another agency, contractor, or other source.-->

#### 連邦情報処理規格 (FIPS: Federal Information Processing Standard)

Information Technology Management Reform Act (Public Law 104-106)に基づいて、商務長官は、連邦政府機関のコンピュータ・システムに適用するために国立標準技術研究所(NIST)が開発した標準及びガイドラインを承認する。これらの標準及びガイドラインは、NISTによってFIPSとして発行されたものであり、政府機関で横断的に使われるものである。
NISTは、セキュリティや相互運用性といった強制力のある連邦政府の要求事項がある場合や、許容可能な業界標準やソリューションが存在しない場合に、FIPSを開発する。詳細については背景を参照すること。

<!--
Under the Information Technology Management Reform Act (Public Law 104-106), the Secretary of Commerce approves standards and guidelines that are developed by the National Institute of Standards and Technology (NIST) for Federal computer systems. These standards and guidelines are issued by NIST as Federal Information Processing Standards (FIPS) for use government-wide. NIST develops FIPS when there are compelling Federal government requirements such as for security and interoperability and there are no acceptable industry standards or solutions. See background information for more details.-->

FIPS文書は、FIPSホームページ <http://www.nist.gov/itl/fips.cfm> からオンラインで利用できる。

<!--
FIPS documents are available online through the FIPS home page: <http://www.nist.gov/itl/fips.cfm>
-->

<!--#### Hash Function-->

#### ハッシュ関数 (Hash Function)

任意長の短いの文字列を、固定長の文字列に変換する関数。承認されているハッシュ関数は以下の性質を満たす。

<!--A function that maps a bit string of arbitrary length to a fixed length bit string. Approved hash functions satisfy the following properties:-->

<!--1. (One-way) It is computationally infeasible to find any input that
                                                                                         maps to any pre-specified output, and-->
   <!--2. (Collision resistant) It is computationally infeasible to find any two distinct inputs that map to the same output.-->

1. (一方向性) 指定された出力結果から、対応する入力を特定することが計算上困難で、
2. (衝突困難性) 同じ出力となる任意の2つの異なる入力を特定することが計算上困難である

<!--#### Holder-of-Key Assertion-->

#### Holder-of-Keyアサーション (Holder-of-Key Assertion)

加入者が保持している対称鍵または（秘密鍵に対応する）公開鍵への参照を含んだアサーション。
RPは、加入者が実際にその鍵を所有・管理することが可能である、ということを検証することで、加入者を認証しても良い。

<!--An assertion that contains a reference to a symmetric key or a public key (corresponding to a private key) held by the subscriber. The RP may authenticate the subscriber by verifying that he or she can indeed prove possession and control of the referenced key.-->

<!--#### Identity-->

#### アイデンティティ (Identity)

与えられた文脈において、人物を一意に指し示す属性の集合。

<!--A set of attributes that uniquely describe a person within a given context.-->


<!--#### Identity Assurance Level (IAL)-->

#### アイデンティティ保証レベル (IAL: Identity Assurance Level)

申請者が申告したアイデンイティが、彼ら自身の実際のアイデンティティに一致することの信頼の度合いを表現する尺度。

<!-- A metric describing degree of confidence that the Applicant’s Claimed Identity is their real identity. -->

<!-- #### Kerberos -->

#### Kerberos

MITで開発された認証プロトコルで幅広く利用されている。古典的なKerberosでは、ユーザは秘密のパスワードをKey Distribution Center(KDC)に共有する。ユーザAliceは、他のユーザBobと通信するため、KDCに対して認証を行い、KDCからチケットの提供を受ける。
そのチケットは、Bobとの間で認証を行うために利用する。

<!--A widely used authentication protocol developed at MIT. In “classic” Kerberos, users share a secret password with a Key Distribution Center (KDC). The user, Alice, who wishes to communicate with another user, Bob, authenticates to the KDC and is furnished a “ticket” by the KDC to use to authenticate with Bob.-->

Kerberos認証はパスワードに基づいており、プロトコルは最初にユーザとKDCの間で行われるやり取りを盗聴することにより可能となる、オフラインの辞書攻撃に対して脆弱であることが知られている。パスワードをより長く・複雑にすることで、この脆弱性に対する一定の緩和策となる一方、十分に長いパスワードはユーザにとって扱いにくいものとなってしまう。

<!--When Kerberos authentication is based on passwords, the protocol is known to be vulnerable to offline dictionary attacks by eavesdroppers who capture the initial user-to- KDC exchange. Longer password length and complexity provide some mitigation to this vulnerability, although sufficiently long passwords tend to be cumbersome for users.-->


<!--#### Knowledge Based Authentication-->

#### 知識ベース認証 (Knowledge Based Authentication)

当人が主張している公のデータベースに記録されているアイデンティティと関連付けられた情報に関する知識に基づいて行われる個人に対する認証。
そのような情報に関する知識は、機密というよりはむしろ内密という程度のものである、と考えられる。なぜならば、知識は、検証主体に対して実施する認証以外の文脈で利用されることがあり、認証プロセスに関連付けられる全体的な確実性を減ずるためである。

<!--Authentication of an individual based on knowledge of information associated with his or her claimed identity in public databases. Knowledge of such information is considered to be private rather than secret, because it may be used in contexts other than authentication to a verifier, thereby reducing the overall assurance associated with the authentication process.-->

#### 中間者攻撃 (MitM: Man-in-the-Middle Attack)

<!--#### Man-in-the-Middle Attack (MitM)-->

認証プロトコルの実行にあたり、攻撃者が、認証の要求主体と検証主体との間に立ち、送受信されるデータを横取り・改ざんする攻撃。

<!--An attack on the authentication protocol run in which the attacker positions himself or herself in between the claimant and verifier so that he can intercept and alter data traveling between them.-->

<!--#### Message Authentication Code (MAC)-->

#### メッセージ認証コード (MAC: Message Authentication Code)

暗号理論に基づくデータのチェックサムであり、対称鍵を用いて、データの予期していない変更及び意図的な変更との両方を検知するために用いられる。MACは真正性(authenticity)と一貫性(integrity)の保護を行うが、非否認性(non-repudiation)は保護は行わない。

<!--A cryptographic checksum on data that uses a symmetric key to detect both accidental and intentional modifications of the data. MACs provide authenticity and integrity protection, but not non-repudiation protection.-->


<!--#### Multi-Factor-->

#### 多要素 (Multi-Factor)

2つ以上の認証要素を利用するような認証システムや認証器の性質。

認証要素の3つのタイプは、本人が知っていること(something you know)、本人が所持しているもの(something you have)、本人に備わっているもの(something you are)である。

<!--
A characteristic of an authentication system or an authenticator that uses more than one authentication factor.
The three types of authentication factors are something you know, something you have, and something you are.-->


<!--#### Network-->

#### ネットワーク (Network)

オープンコミュニケーションの媒介、典型的にはインターネットであり、要求者と対応する関係者間でメッセージを伝送するために利用されるもの。
特別に宣言をしていない限り、ネットワークのセキュリティについては何ら仮定は行わないものとする。
すなわち、オープンであり、関係者（例：要求者、検証主体、CSP、RP）間の任意の地点で、能動的攻撃(例：なりすまし、中間者、セッションハイジャック）と受動的攻撃(例：盗聴）に晒されている、と仮定する。

<!--
An open communications medium, typically the Internet, that is used to transport messages between the claimant and other parties. Unless otherwise stated, no assumptions are made about the security of the network; it is assumed to be open and subject to active (i.e., impersonation, man-in-the-middle, session hijacking) and passive (i.e., eavesdropping) attack at any point between the parties (e.g., claimant, verifier, CSP or RP).-->

#### ノンス (Nonce)

<!--#### Nonce-->

セキュリティプロトコル中で利用され、同じキーによる繰り返しを許さない値。例えば、ノンスはチャレンジ・レスポンス認証プロトコルのチャレンジとして利用され、認証キーが変更されるまでの間、繰り返されないものとする(SHALL NOT)。
さもなければ、再生攻撃(replay attack)の可能性がある。
ノンスをチャレンジとして利用することと、チャレンジをランダムにすることとは異なる要件である。というのも、ノンスは必ずしも予測不可能である必要性がないからである。

<!-- SHALL notとなっており小文字になっているので要指摘-->

<!--A value used in security protocols that is never repeated with the same key. For example, nonces used as challenges in challenge-response authentication protocols SHALL not be repeated until authentication keys are changed. Otherwise, there is a possibility of a replay attack. Using a nonce as a challenge is a different requirement than a random challenge, because a nonce is not necessarily unpredictable.-->

<!--#### Offline Attack-->

#### オフライン攻撃 (Offline Attack)

攻撃者が何らかの情報を得る（典型的には認証プロトコルの実行を盗聴したり、システムに侵入してセキュリティファイルを盗む）ことで、選択したシステムを分析する攻撃。

<!--An attack where the attacker obtains some data (typically by eavesdropping on an authentication protocol run or by penetrating a system and stealing security files) that he/she is able to analyze in a system of his/her own choosing.-->

<!--#### Online Attack-->

#### オンライン攻撃 (Online Attack)

認証プロトコルにおいて、正当な認証主体に対する要求者の役割を詐称する、または能動的に認証チャネルを改ざんする攻撃。

<!--
An attack against an authentication protocol where the attacker either assumes the role of a claimant with a genuine verifier or actively alters the authentication channel.-->

<!-- #### Online Guessing Attack -->

#### オンライン推測攻撃 (Online Guessing Attack)

<!--An attack in which an attacker performs repeated logon trials by guessing possible values of the authenticator output.-->

攻撃者が認証器の出力が取りうる値を推測して、ログオンを繰り返し行うような攻撃。

<!-- #### Passive Attack -->

#### 受動的攻撃 (Passive Attack)
認証プロトコルに対する攻撃。要求者と検証主体との間をネットワークを介してやり取りされるデータを傍受するが、データは改ざんしない(例. 盗聴)。

<!-- An attack against an authentication protocol where the attacker intercepts data traveling along the network between the claimant and verifier, but does not alter the data (i.e., eavesdropping).-->

<!--
#### Password
A secret that a claimant memorizes and uses to authenticate his or her identity. Passwords are typically character strings.
-->

#### パスワード (Password)
要求者が記憶し、自身のアイデンティティを認証するために利用するシークレット。パスワードは一般的に、文字列である。

#### Personal Identification Number (PIN)
数字のみで構成されているパスワード。

<!-- A password consisting only of decimal digits.-->

#### Personal Identity Verification (PIV) Card
Personal Identity Verification (PIV) カードは \[FIPS 201\]で定義された物理的な人工物(例. IDカード、スマートカード)であり、連邦政府の職員や契約業者に対して発行される。クレデンシャル(例. 写真、暗号鍵、デジタル化した指紋)を含んでおり、カード所有者が主張するアイデンティティは、あらかじめ保存してあるクレデンシャルと比較することで、他者による検証(人間による読み取り、検証)や、自動化手続きによる検証(コンピュータによる読み取り、検証)が可能である。

<!--
Defined by \[FIPS 201\] as a physical artifact (e.g., identity card, smart card) issued to federal employees and contractors that contains stored credentials (e.g., photograph, cryptographic keys, digitized fingerprint representation) so that the claimed identity of the cardholder can be verified against the stored credentials by another person (human readable and verifiable) or an automated process (computer readable and verifiable).
-->

<!--
#### Pharming
An attack in which an attacker corrupts an infrastructure service such as DNS (Domain Name Service) causing the subscriber to be misdirected to a forged verifier/RP, which could cause the subscriber to reveal sensitive information, download harmful software or contribute to a fraudulent act.
-->

#### ファーミング (Pharming)
DNS(Domain Name Service) のようなインフラストラクチャサービスを汚染する手法により、加入者を偽造した検証主体/RPへ誘導し、機微情報を入力させる、有害なソフトウェアをダウンロードさせる、詐欺活動に加担させる可能性のある攻撃。

<!--
#### Phishing
An attack in which the subscriber is lured (usually through an email) to interact with a counterfeit verifier/RP and tricked into revealing information that can be used to masquerade as that subscriber to the real verifier/RP.
-->

#### フィッシング (Phishing)
加入者を(主にemailを通じて)偽の検証主体/RPに誘導し、真の検証主体/RPに対して加入者に成りすましを行うために利用する情報を騙し取る攻撃。

<!--
#### Possession and control of an authenticator
The ability to activate and use the authenticator in an authentication protocol.
-->

#### 認証器の所有および管理 (Possession and control of an authenticator)
認証プロトコルにおいて、認証器をアクティベートし、利用できること。


<!--
#### Practice Statement
A formal statement of the practices followed by the parties to an authentication process (i.e., RA, CSP, or verifier). It usually describes the policies and practices of the parties and can become legally binding.
-->

#### 実施規定 (Practice Statement)
認証プロセスの当事者(例. RA、CSP、検証主体)が従う実践的な内容を正式に記載した文書。通常、当事者のポリシーと実行内容が記述されており、法的拘束力を持つ可能性がある。

<!--
#### Private Credentials
Credentials that cannot be disclosed by the CSP because the contents can be used to compromise the authenticator.
-->

#### プライベートクレデンシャル (Private Credentials)
認証器を損なうために使うことができるため、CSPによって開示されることがないクレデンシャル。

<!--
#### Private Key
The secret part of an asymmetric key pair that is used to digitally sign or decrypt data.
-->

#### 秘密鍵 (Private Key)
非対称鍵ペアの秘密である側。デジタル署名やデータ暗号化に用いる。

<!--
#### Protected Session
A session wherein messages between two participants are encrypted and integrity is protected using a set of shared secrets called session keys.
-->
<!--
A participant is said to be *authenticated* if, during the session, he, she or it proves possession of an authenticator in addition to the session keys, and if the other party can verify the identity associated with that authenticator. If both participants are authenticated, the protected session is said to be *mutually authenticated*.
-->

#### 保護されたセッション (Protected Session)
セッション鍵と呼ばれる共通シークレット一式を用いて、二者間のメッセージが暗号化され、一貫性が保護されるようなセッション。

セッションが継続する間において、セッション鍵に加えて当事者が認証器の所持を証明する、または他方が認証器に関連付けられたアイデンティティを検証することができるならば、当事者が *認証済み(authenticated)* であるという。もし相互の当事者が認証済みである場合、保護されたセッションは *相互に認証済み(mutually authenticated)* と呼ばれる。

<!--
#### Public Credentials
Credentials that describe the binding in a way that does not compromise the authenticator.
-->

#### パブリッククレデンシャル (Public Credentials)
認証器を損なうことのない方法で紐付けされているクレデンシャル。

<!--
#### Public Key
The public part of an asymmetric key pair that is used to verify signatures or encrypt data.
-->

#### 公開鍵 (Public Key)
非対称鍵ペアの公開側。署名検証やデータ復号に用いる。

<!--
#### Public Key Certificate
A digital document issued and digitally signed by the private key of a certificate authority that binds the name of a subscriber to a public key. The certificate indicates that the subscriber identified in the certificate has sole control and access to the private key. See also [[RFC 5280]](#RFC5280).
-->

#### 公開鍵証明書 (Public Key Certificate)
加入者の名前と公開鍵を紐付けている認証局(CA)の秘密鍵でデジタル署名され発行されるデジタル文書。証明書は、証明書中で識別される加入者が、唯一、その秘密鍵のコントロールとアクセスがであることを示す。 [[RFC 5280]](#RFC5280) も参照のこと。



#### Public Key Infrastructure (PKI)
発行、維持、証明書、公開-秘密の鍵ペアの管理のために用いるポリシー、プロセス、サーバプラットフォーム、ソフトウェア、およびワークステーションのこと。

<!--
A set of policies, processes, server platforms, software and workstations used for the purpose of administering certificates and public-private key pairs, including the ability to issue, maintain, and revoke public key certificates.
-->

#### 登録 (Registration)
申請者がCSPの加入者となり、CSPが申請者のアイデンティティの正当性を確認するプロセス。

<!--
The process through which an Applicant applies to become a subscriber of a CSP and the CSP validates the identity of the Applicant.
-->

#### Relying Party (RP)
加入者の認証器とクレデンシャル、または検証主体が発行する要求者のアイデンティティのアサーションを信頼し、一般的には、取引を進めたり、情報やシステムへのアクセス権限を与えたりするエンティティ。

<!--
An entity that relies upon the subscriber's authenticator and credentials or a verifier's assertion of a claimant’s identity, typically to process a transaction or grant access to information or a system.
-->

#### リモート (Remote)
(*リモート認証やリモート取引で*)ネットワークで繋がったデバイス間で交換される情報。その情報は、単一の組織のセキュリティ統制によるエンドツーエンドの信頼できる保護ができない。

<!--
#### Remote
(*As in remote authentication or remote transaction*) An information exchange between network-connected devices where the information cannot be reliably protected end-to-end by a single organization’s security controls.
-->

注記: インターネット上でやり取りされる全ての情報は、リモートである、と考える。

<!--
Note: Any information exchange across the Internet is considered remote.
-->


#### リプレイ攻撃 (Replay Attack)
攻撃者が、正当な申請者と検証主体との間のメッセージをキャプチャし、申請者から検証主体、またはその逆であるかのように振る舞うために再送できるような攻撃。

<!--
#### Replay Attack
An attack in which the attacker is able to replay previously captured messages (between a legitimate claimant and a verifier) to masquerade as that claimant to the verifier or vice versa.
-->

#### リスクアセスメント (Risk Assessment)
システム・セキュリティに対するリスクを識別し、発生確率、与える影響、影響を緩和しうる追加の防御策を決定するプロセス。リスクマネジメント及びリスク分析と同義のものの一部。

<!--
#### Risk Assessment
The process of identifying the risks to system security and determining the probability of occurrence, the resulting impact, and additional safeguards that would mitigate this impact. Part of Risk Management and synonymous with Risk Analysis.
-->

#### ソルト (Salt)
暗号プロセスにおいて用いられる秘密でない(non-secret)値で、通常、ある特定の計算結果が攻撃者によって再利用されないことを保証するために用いられる。

<!--
#### Salt
A non-secret value that is used in a cryptographic process, usually to ensure that the results of computations for one instance cannot be reused by an attacker.
-->

#### 二次認証器 (Secondary Authenticator)
アサーションプロトコルの一部分において、正しく認証された加入者を検証することで発行された一時的なシークレット。このシークレットは発行後、加入者がRPに対して認証するために利用する。

二次認証器の例としては、無記名アサーション、アサーション参照、及びKerberosセッションキーがある。

<!--
#### Secondary Authenticator
A temporary secret, issued by the verifier to a successfully authenticated subscriber as part of an assertion protocol. This secret is subsequently used, by the subscriber, to authenticate to the RP.
-->
<!--
Examples of secondary authenticators include bearer assertions, assertion references, and Kerberos session keys.
-->

#### Secure Sockets Layer (SSL)

*Transport Layer Security (TLS)* を参照のこと。

<!--
See *Transport Layer Security (TLS)*.
-->


#### Security Assertion Mark-up Language (SAML)
OASIS(Organization for the Advancement of Structured Information Standards)によって開発されたXMLベースのセキュリティ仕様で、信頼されたエンティティ間がインターネット上で、認証（及び認可）情報を交換するために利用される。\[[SAML](#SAML)\]を参照のこと。

<!--
An XML-based security specification developed by the Organization for the Advancement of Structured Information Standards (OASIS) for exchanging authentication (and authorization) information between trusted entities over the Internet. See \[[SAML](#SAML)\].
-->


<!--
#### SAML Authentication Assertion
A SAML assertion that conveys information from a verifier to an RP about a successful act of authentication that took place between the verifier and a subscriber.
-->

#### SAML認証アサーション (SAML Authentication Assertion)
検証主体と加入者の間で行われた成功した認証行為について、検証主体からRPに対して情報を伝達するSAMLアサーションの一つ。

#### セッション (Session)
加入者とエンドポイント、またはRPやCSPとの間の継続的なインタラクション。セッションは認証イベントで開始し、セッション終了イベントで終了する。セッションは、加入者のソフトウェア(ブラウザ、アプリケーションやOS）がRPやCSPに対して、加入者の認証クレデンシャルの代わりに提示するセッションシークレットを用いて結び付けられる。

<!--
#### Session
A persistent interaction between a subscriber and an endpoint, either an RP or a CSP. A session begins with an authentication event and ends with a session termination event. A session is bound by use of a session secret that the subscriber's software (a browser, application, or OS) can present to the RP or CSP in lieu of the subscriber's authentication credentials.
-->

#### セッションハイジャック攻撃 (Session Hijack Attack)
攻撃者が自身を申請者と検証主体の間に入り込み、その後、当事者間で認証を成功させるような攻撃。攻撃者は検証主体に対して加入者であるかのように振る舞うことができ、逆にセッションデータののやり取りを制御することもできる。申請者とRP間のセッションも同様に侵害される可能性がある。

<!--
#### Session Hijack Attack
An attack in which the attacker is able to insert himself or herself between a claimant and a verifier subsequent to a successful authentication exchange between the latter two parties. The attacker is able to pose as a subscriber to the verifier or vice versa to control session data exchange. Sessions between the claimant and the Relying Party can also be similarly compromised.
-->

#### シェーアド・シークレット (Shared Secret)
申請者と検証主体にとっては既知である認証で使用する秘密。

<!--
#### Shared Secret
A secret used in authentication that is known to the claimant and the verifier.
-->

#### サイドチャネル攻撃 (Side Channel Attack)
物理的な暗号システムからの情報漏洩によって可能となる攻撃。タイミング、消費電力、電磁波放出はサイドチャネル攻撃で活用されうる特徴の例である。

<!--
#### Side Channel Attack
An attack enabled by leakage of information from a physical cryptosystem. Timing, power consumption, and electromagnetic emissions are examples of characteristics that could be exploited in a side-channel attack.
-->

#### ソーシャルエンジニアリング (Social Engineering)
ある個人と親交を深めて信用・信頼を得ることによって、個人を騙して個人の機微情報を明らかにする行為。

<!--
#### Social Engineering
The act of deceiving an individual into revealing sensitive information by associating with the individual to gain confidence and trust.
-->

#### Special Publication (SP)
NISTによって発行される出版物。特に、Special Publication 800シリーズは、Information Technology Laboratoryの研究、ガイドライン、及びコンピュータセキュリティにおける教育・援助を行う努力、さらに産業、政府、及び学術機関との協調的な活動についての報告である。

<!--
A type of publication issued by NIST. Specifically, the Special Publication 800-series reports on the Information Technology Laboratory's research, guidelines, and outreach efforts in computer security, and its collaborative activities with industry, government, and academic organizations.
-->

#### 強結合クレデンシャル (Strongly Bound Credentials)
改ざんの痕跡が残る方法で加入者と結びつけられたクレデンシャル。

<!--
#### Strongly Bound Credentials
Credentials that are bound to a subscriber in a tamper-evident fashion.
-->

#### 加入者 (Subscriber)
CSPから認証器に結びつけられたクレデンシャルを受け取る当事者。

<!--
#### Subscriber
A party who has received a credential bound to an authenticator from a CSP.
-->

#### 対象鍵 (Symmetric Key)
暗号化と複合、またはメッセージ認証コードの作成と検証に例示される暗号操作及びその逆操作の両方を実施するために利用する鍵。

<!--
#### Symmetric Key
A cryptographic key that is used to perform both the cryptographic operation and its inverse, for example to encrypt and decrypt, or create a message authentication code and to verify the code.
-->

#### トークン (Token)
*認証器* を参照のこと。

<!--
#### Token
See *Authenticator*.
-->

### トークン認証器 (Token Authenticator)
*認証器出力* を参照のこと。

<!--
#### Token Authenticator
See *Authenticator Output*.
-->

<!-- TODO: Token Output??? -->

#### トークンシークレット (Token Secret)
*認証器シークレット* を参照のこと。

<!--
#### Token Secret
See *Authenticator Secret*.
-->

#### Transport Layer Security (TLS)
ブラウザやウェブサーバに広く実装されている認証・セキュリティプロトコル。TLSは [[RFC 5246]](#RFC5246) で定義されている。TLSはより古い Secure Socket Layer (SSL)プロトコルと、実質的にSSLバージョン3.1であるTLS1.0と同様である。NIST [[SP 800-52]](#SP800-52) ガイドラインでは、Transport Layer Security (TLS)実装の選択と利用について記載しており、TLSを政府のアプリケーションでどのように利用すべきであるかを指定している。

<!--
An authentication and security protocol widely implemented in browsers and web servers. TLS is defined by [[RFC 5246]](#RFC5246). TLS is similar to the older Secure Sockets Layer (SSL) protocol, and TLS 1.0 is effectively SSL version 3.1. NIST [[SP 800-52]](#SP800-52), *Guidelines for the Selection and Use of Transport Layer Security (TLS) Implementations* specifies how TLS is to be used in government applications.
-->

#### トラストアンカー (Trust Anchor)
公開鍵・共通鍵が、別の（例えば公開鍵証明書で）信頼されている存在によって保証されているよりむしろ、直接的に、ハードウェアやソフトウェアに組み込まれた、セキュアに経路外の方法でプロビジョニングされている、といった理由で信頼されていること。

<!--
#### Trust Anchor
A public or symmetric key that is trusted because it is directly built into hardware or software, or securely provisioned via out-of-band means, rather than because it is vouched for by another trusted entity (e.g. in a public key certificate).
-->

#### 検証主体 (Verifier)
認証プロトコルを利用して、1つまたは2つの認証器を申請者が所有、管理できることを検証し、申請者のアイデンティティを検証する存在。

<!--
#### Verifier
An entity that verifies the claimant’s identity by verifying the claimant’s possession and control of one or two authenticators using an authentication protocol. To do this, the verifier may also need to validate credentials that link the authenticator(s) and identity and check their status.
-->

#### 検証主体なりすまし攻撃 (Verifier Impersonation Attack)
認証プロトコルにおいて、攻撃者が検証主体になりすまし、一般的には真の検証主体に対して加入者を詐称することを目的として情報を集めるようなシナリオ。

<!--
#### Verifier Impersonation Attack
A scenario where the attacker impersonates the verifier in an authentication protocol, usually to capture information that can be used to masquerade as a subscriber to the real verifier.
-->

#### 弱結合クレデンシャル (Weakly Bound Credentials)
クレデンシャルを無効化することなく改ざんできてしまう方法で、加入者と結びつけられたクレデンシャル。

<!--
#### Weakly Bound Credentials
Credentials that are bound to a subscriber in a manner than can be modified without invalidating the credential.
-->

#### ゼロ化 (Zeroize)
データを破壊し、復元できないようにするために、ゼロ値のビットだけで構成されるデータによってメモリを上書きすること。これはしばしば、データそのものを破壊するのではなく、ファイルシステム上のデータへの参照を破壊するだけの削除手法と対比される。

<!--
#### Zeroize
Overwrite a memory location with data consisting entirely of bits with the value zero so that the data is destroyed and not recoverable. This is often contrasted with deletion methods that merely destroy reference to data within a file system rather than the data itself.
-->

#### ゼロ知識パスワードプロトコル (Zero-knowledge Password Protocol)
申請者が検証主体に対して認証を行う際、検証主体に対してパスワードを提示する必要がないようなパスワードベースの認証プロトコル。
プロトコルの例としては、EKE、SPEKE及びSRPがある。

<!--
#### Zero-knowledge Password Protocol
A password based authentication protocol that allows a claimant to authenticate to a verifier without revealing the password to the verifier. Examples of such protocols are EKE, SPEKE and SRP.
-->