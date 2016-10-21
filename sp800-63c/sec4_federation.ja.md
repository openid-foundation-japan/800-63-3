<a name="sec4"></a>

## 4. Federation

Identity / Authentication Information を一連のネットワークシステム間でやりとりするためのプロセス.
Federation シナリオでは, Verifier / CSP は *Identity Provider* や IdP と呼ばれる. また本ドキュメントでは *Relying Party* や RP は Federated Identity を受け取る主体である.

<!-- Federation is a process that allows for the conveyance of identity and authentication information across a set of networked systems. In a federation scenario, the verifier or CSP is known as the *identity provider*, or IdP. In this document, the *relying party*, or RP, is the party that receives the federated identity. -->

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 1: Federation](sp800-63c/media/federation.png)

**Figure 4-1: Federation**

</div>

Federation Protocol では, Subscriber, IdP, RP の3者間で三角形の関係がなりたつ (([Figure 4-1](#63cSec4-Figure1)).
プロトコルによっては, 異なるタイミングで異なる情報が各辺を流れることもある.
Subscriber は, 通常は Web Browser を通じて IdP, RP 双方とやり取りを行う.
RP と IdP の間のやりとりは, (Subscriber が関与するリダイレクト経由で) Front Channel で行われることもあれば, Back-channel で (Direct Connection を通じて) 行われることもあり, (暗号論的に保護された Self-contained Assertion などのように) パッケージ化された情報を通じて行われることもある.

<!-- In a federation protocol, a triangle is formed between the subscriber, the IdP, and the RP ([Figure 4-1](#63cSec4-Figure1). Depending on the specifics of the protocol, different information passes across each leg of the triangle at different times. The subscriber communicates with both the IdP and the RP, usually through a web browser. The RP and the IdP communicate with each other, though this communication can happen over the front channel (through redirects involving the subscriber), over the back channel (through a direct connection), or via a packaged information bundle (such as a cryptographically protected and self-contained assertion). -->

Subscriber は IdP に対して何らかの Primary Credential を使って自身を認証し, その Authentication Event はネットワーク経由で RP に対して Assert される.
IdP はこのプロセスを通じて Subscriber に関する Attribute Statement を生成することも可能である.
この Attribute および Authentication Event は通常 Assertion を利用して RP に伝えられる. (Section 5 参照)

<!-- The subscriber authenticates to the IdP using some form of primary credential, and then that authentication event is asserted to the RP across the network. The IdP can also make attribute statements about the subscriber as part of this process. These attributes and authentication event information are usually carried to the RP through the use of an assertion (see section 5.). -->

RP と IdP とのやりとりは, Subscriber がトランザクションを行う IdP には明示される.
複数の RP とやりとりする IdP は Subscriber のトランザクションをプロファイリングすることも可能となる.
これは Federation 無しには不可能であったろう.
これは Subscriber の Privacy Interest にそぐわない形での Subscriber Tracking や Profile Information の利用につながりかねない.

<!-- The RP communication with the IdP reveals to the IdP where the subscriber is conducting a transaction. Communications from multiple RPs allow the IdP to build a profile of subscriber transactions that would not have existed absent federation. This aggregation could enable new capabilities for subscriber tracking and use of profile information that do not align with the privacy interests of the subscribers.  -->

IdP は RP 上での Subscriber のアクティビティを第三者に漏らすべきではなく (SHALL NOT), Federated Authentication 目的や法的手続き, 当該ユーザーからの要望による以外でそういった情報を利用すべきでもない (SHALL NOT).
IdP は Subscriber Tracking や Profiling を防止したり Unlinkability を確保するための技術的対策を行うべきである (SHOULD).

<!-- The IdP SHALL NOT disclose information on subscriber activities at an RP to any party, nor use the information for any purpose other than federated authentication, to comply with law or legal process, or in the case of a specific user request for the information. The IdP SHOULD employ technical measures to provide unlinkability and prevent subscriber activity tracking and profiling. -->

IdP は, Subscriber アカウントへの不正ログイン発生時など, セキュリティ目的であれば, Federation の範囲内で他の RP に Subscriber のアクティビティを公表することもできる (MAY).

<!-- A IdP MAY disclose information on subscriber activities to other RPs within the federation for security purposes such as communication of compromised subscriber accounts. -->

各機関には以下の要件が課せられる.

<!-- The following requirements apply specifically to agencies: -->

a) Senior Agency Official for Privacy と協議の上, Privacy Act の要件に照らして, 自身が Identity Federation において IdP となるか RP となるかを分析, 決定する (SHALL).

<!-- a) The agency SHALL consult with their Senior Agency Official for Privacy to conduct and analysis to determine whether the agency acting as either an IdP, or an RP in an identity federation triggers the requirements of the Privacy Act. -->

b) 適宜 System of Records Notice を公開, ないしは適用範囲を特定する (SHALL).

<!-- b) The agency SHALL publish, or identify coverage by a System of Records Notice as applicable. -->

c) Senior Agency Official for Privacy と協議の上, E-Government Act の要件に照らして, 自身が Identity Federation において IdP となるか RP となるかを分析, 決定する (SHALL).

<!-- c) The agency SHALL consult with their Senior Agency Official for Privacy to conduct an analysis to determine whether the agency acting as either an IdP, or an RP in an identity federation triggers the requirements of the E-Government Act. -->

d) 適宜 Privacy Impact Assessment を公開, ないしは適用範囲を特定する (SHALL).

<!-- d) The agency SHALL publish or identify coverage by a Privacy Impact Assessment, as applicable. -->

### 4.1. Federation Models

本セクションでは, 現在使われているいくつかの Identity Federation の一般的モデルを概観する.
これらのモデルでは, Federation 参加者間の関係性確立方法が複数種類存在する.
なかには等しく高レベルの Trust を必須とするモデルもあり, 多様な Trust Relationship を認めるモデルもある.

<!-- This section provides an overview of a few common models of identity federation currently in use. In these models, a relationship is established between members of the federation in several different ways. Some models mandate that all federated parties have an equally high level of trust, while other models allow for parties with a diversity of relationships. -->

#### 4.1.1 Central Authority

Central Authority に従って, 関係各所と相互にメタデータのやりとりを行う Federated Party も存在する.
そういったモデルでは, Central Authority は Federation を行う各主体に対して一定レベルの審査を行い, Security および Integrity Standard に対する準拠を求めることが多い.

<!-- Some federated parties defer to a central authority to make decisions for them and to communicate metadata between parties. In this model, the central authority generally conducts some level of vetting on each party in the federation to verify compliance with predetermined security and integrity standards. -->


Central Authority モデルを用いた Federation の多くでは, Federation に参加しているか否かというシンプルなメンバーシップモデルを採用している.
しかしながら, より洗練した Federation ではより細かなメンバーシップレベルを持ち, より細かく徹底した審査を通過した主体やより高いアクセスレベルを満たす主体を扱うことができる.
結果として, Federation 参加者が高レベルのメンバーに対して Subscriber の情報を自動的に渡すといったことも可能になる

<!-- Most federations using the central authority model have a simple membership model - either parties are in the federation or they are not. However, more sophisticated federations have multiple tiers of membership which can be used by federated parties to tell whether other parties in the federation have been more thoroughly vetted or have some common purpose that justifies a higher level of access. As a consequence, some parties in the federation are more likely to automatically release information about their subscribers to the parties in the higher tiers. -->

#### 4.1.2 Manual Registration

Manual Registration モデルでは, System Administorator がメタデータを扱い, システムの相互接続性をテストしたのち, 実際に User Transaction を開始させる.
Federation に参加する主体に関するメタデータは Federated Party のレジストリに手動入力される.
各主体は個別に自身が Federation を行いたい相手を登録したレジストリを管理する.

<!-- In the manual registration model of federation, system administrators communicate metadata and test system interoperability before transactions take place between users over the wire. Metadata for each party who wishes to participate is manually input into a registry of federated parties. Each party maintains their own registry of other parties with whom they wish to federate. -->

Manual Registration は, Authority や Federation Operator の関与無しに, 個別に行うことができる.
この場合, IdP と RP の間で IdP と RP の間には相互の関連性が確立される.

<!-- Manual registration can take place on a case by case basis without any authority or federation operator in place. In this case, a pairwise relationship is created between the IdP and the RP. -->

Manual Registration は Central Authority モデルと合わせて利用することもできる.
その場合, Central Authority に既知の主体を含んだレジストリが事前に構築され, それ以降は必要に応じて手動でのレジストリ登録が行われることになる.

<!-- Manual registration can also work in concert with a central authority model. In this case, a registry is pre-populated with parties known to the central authority, and more parties are added manually on an as-needed basis. -->

#### <a name="dynamic-registration"></a> 4.1.3 Dynamic Registration

Dynamic Registration モデルでは, 各システムはその他のシステムが当該システムのメタデータを取得できるように well-known location エンドポイントを持つ.
また新しいシステムが人間の関与無しに自身を登録できるよう, 予測可能な形で API エンドポイントも提供する.
Dynamic Registration を使うシステムは, Subscriber に IdP 上で Identity Federation Transaction に対する明示的許可を要求するなど, 人間が関与する検証ステップを設けるべきである (SHOULD).

<!-- In the dynamic registration model of federation, systems have a well-known location where other systems can find their metadata. They also have predictable API endpoints where new systems can register themselves without human involvement. Systems that make use of dynamic registration SHOULD require verifiable human interaction, such as the approval of the identity federation transaction by the authenticated subscriber at the IdP. -->

各 Federated Party は, その他の Federated Party に対して, Attribute やその他の情報に関するアクセスポリシーを設定する.
Dynamic Registration 環境では, 新しく登録された主体は Authorized Party のレビューを通過するまで非常に限定されたアクセスのみが可能となることもある.
例えば, システム管理者などがより高いアクセスレベルを許可するケースなどがありうる.
さらに Dynamic Registration により登録された主体は往々にして Authentication Transaction 中に Subscriber による Authorization を必要とすることになる.
([Runtime Decisions](#runtime-decisions) 参照)

<!-- Each federated party sets attribute and information access policies for other federated parties. In a dynamic registration environment, a newly registered party could be severely limited in its access until such time as it is reviewed by an authorized party. For instance, a system administrator can grant higher levels of access. Additionally, a dynamically registered party will usually also require authorization from a subscriber during the authentication transaction (see [Runtime Decisions](#runtime-decisions)). -->

Dynamic Registration モデルでは, 各主体は事前に相互の関係性を確立できないことが多く, デフォルトではあまり多くの情報をやりとりしないことが多い.
この問題は, Software Statement と呼ばれる技術を用いれば, ある程度改善される.
Software Statement とは, Dynamic Registration に関与した主体に関する属性を暗号論的に検証可能とするものである.
Software Statement は RP Software に関する属性のリストであり, 認証機関により暗号論的に署名されている.
認証機関を信頼する主体は, 認証機関に対する Trust を Dynamic Registration によって確立したパートナーシップに対しても拡張できる.
これにより, self-asserted な属性のみに依存せず, Federated Party 間でコネクションを確立したり強めたりすることができる.
詳細は [[RFC 7591]](#RFC7591) Section 2.3 を参照のこと.

<!-- Frequently, parties in a dynamic registration model have no way to know each other ahead of time. As a consequence, little information about users and systems is exchanged by default. This problem is somewhat mitigated by a technology called software statements, which allow federated parties to cryptographically verify some attributes of the parties involved in dynamic registration. Software statements are lists of attributes describing the RP software, cryptographically signed by certifying bodies. Because both parties trust the certifying body, that trust can be extended to the other party in the dynamic registration partnership.  This allows the connection to be established or elevated between the federating parties without relying on self-asserted attributes entirely. See [RFC 7591](#RFC7591) section 2.3 for more information. -->

#### 4.1.4 Proxied Federation

Proxied Federation Model では, IdP と RP は, 2者間の直接的コミュニケーションを禁止する形で Proxy される.
この実現方法は様々であるが, 一般的には "Federation Proxy" (or "Proxy") やネットワーク上の "node" として動作する第三者が介在することになる.

<!-- In a proxied federation model, the communication between the IdP and the RP is proxied in a way that prevents direct communication between the two parties. There may be multiple methods of achieving this effect, but common configurations include a third party that acts as a federation proxy (or "broker") or a network of "nodes" that distribute the communications.  -->

この介在者は片や Federation IdP として動作し, もう片方では Federation RP として動作する.
特に Federation Proxy は全ての Federated RP に対して IdP として動作し, 全ての Federated IdP に対して RP として動作する.
よって IdP および RP に適用される Normative Requirements は, 上記介在者にも同様に適用されるべきである (SHALL).

<!-- Effectively, the parties still function in some degree as a federation IdP on one side and a federation RP on the other side. Notably, a federation proxy acts as an IdP to all federated RPs and as an RP to all federated IdPs. Therefore, all normative requirements that apply to IdPs and RPs SHALL apply to the parties of such a system in their respective roles. -->

<a name="63cSec4-Figure1"></a>

<div class="text-center" markdown="1">
![Figure 2: Federation Proxy](sp800-63c/media/broker.png)

**Figure 4-2: Federation Proxy**
</div>

Proxied Federation Model は多様な利点を持つ.
例えば Federation Proxy は RP と IdP の間でインテグレーションが必要な箇所を削減することで技術的インテグレーションを単純化することもできる.
これは [Dynamic Registration](#dynamic-registration) をサポートしないプロトコルでは有効たりうる.
さらに, Proxied Federation Model は RP と IdP の双方を効果的に blind するため, Subscriber のリストをお互いに開示したくない組織にとってビジネス上の機密性を高める効果もある.
また同様に上述の Federation におけるプライバシーリスクを軽減する効果もある.

<!-- A proxied federation model can provide various benefits. For example, federation proxies can enable simplified technical integrations between the RP and IdP by eliminating the need for multiple point to point integrations, which can be onerous for protocols which do not support [dynamic registration](#dynamic-registration). Additionally, to the extent a proxied federation model effectively blinds the RP and IdP from each other, it can provide some business confidentiality for organizations that may not wish to reveal their subscriber lists to each other, as well as mitigate some of the privacy risks of point to point federation described above.  -->

追加のプライバシー保護策を提供しない実装もあれば, Blinding Technology によって多様なプライバシーレベルを提供する実装もある.
(注: Blinding Technology を利用したとしても, Blind された主体が Timestamp や Cookie, Attribute や Attribute Bundle のサイズなどを解析し, Subscriber の行動を推測することは可能である.)
Privacy Policy で IdP, RP, Federation Proxy による適切なデータ利用を宣言していたとしても, Blinding 技術はデータへのアクセス自体を困難にするため, より効率的である.
しかしながらBlinding レベルが上がると, それに比例して技術的・運用上の複雑度は上昇する.

<!-- While some proxied deployments offer no additional privacy protection (such as those that exist as integration points), others can offer varying levels of privacy to the subscriber through a range of blinding technologies. NOTE: even with the use of blinding technologies, it may still be possible for a blinded party to deduce subscriber behavior patterns through analysis of timestamps, cookies, attributes, or attribute bundle sizes. Privacy policies may dictate appropriate use by the IdP, RP, and the federation proxy, but blinding technology can increase effectiveness of these policies by making the data more difficult to access. It should also be noted that as the level of blinding increases, so does the technical and operational implementation complexity. -->

以下に Blinding 実装のパターンを挙げる. この表は説明用のものであり, 網羅性を持つものでもある技術固有のものではない.

<!-- The following table illustrates a spectrum of blinding implementations. This table is intended to be illustrative, and is neither comprehensive nor technology-specific. -->

<div class="text-center" markdown="1">

**Table 4-1: Federation Proxies**

</div>

|Proxy Type|RP knows IdP|IdP knows RP|Proxy can track subscriptions between RP and IdP|Proxy can see attributes of Subscriber|
|---|---|---|---|---|
|Non-blinding Proxy with Attributes|Yes|Yes|Yes|Yes|
|Non-blinding Proxy|Yes|Yes|Yes|No|
|Double Blind Proxy with Attributes|No|No|Yes|Yes|
|Double Blind Proxy|No|No|Yes|No|
|Triple Blind Proxy|No|No|No|No|

#### 4.1.5 <a name="runtime-decisions"></a>Runtime Decisions

Federated Party が何らかの登録処理や Central な主体による管理によって相互に既知であったとしても, それだけですぐに情報のやりとりが許されるわけではない.
例えば Federated Party の Whitelist を作成し, そういった相手にのみ Subscriber の Runtime Authorization なしで認証連携や Subscriber に関する情報のやり取りを行うこともできる.
また同様に Federated Party の Blacklist を作成し, そういった相手には Subscriber に関する情報を全く渡さないということもありうる.
Whitelist にも Blacklist にもない Federated Party に対しては, デフォルトではグレーゾーンとして扱い, Authorized Party (往々にして Subscriber) による Runtime Authorization を求めることになろう.

<!-- The fact that federated parties are known to each other through some form of registration or centralized management does not necessarily mean they are allowed to pass information. Federated parties can establish whitelists of other federated parties who may authenticate subscribers or pass information about them without runtime authorization from the subscriber. Federated parties can also establish blacklists of other federated parties who may not be allowed to pass information about subscribers at all. Every party that is not on a whitelist or a blacklist is placed by default in a gray area where runtime authorization decisions will be made by an authorized party, often the subscriber. -->

