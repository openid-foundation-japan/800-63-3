---
layout: cover
title: "NIST SP 800-63-3 Digital Authentication Guideline"
description: "Public Preview for NIST Special Publication: SP 800-63-3 Digital Authentication Guideline"
---
<section class="home home-title" markdown="1">

# Digital Authentication Guideline: Public Preview (翻訳版)

</section>
<section class="home home-about" markdown="1">
<div class="section-container" markdown="1">
<div class="section-content" markdown="1">

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63-3.ja.html"><img src="assets/800_63_3_doc.png" alt="SP 800-63-3" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63-3.ja.html">SP 800-63-3</a></h3>
  <h6>Digital Authentication Guideline</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.html"><img src="assets/800_63_3_Proofing.png" alt="SP 800-63A" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.html">SP 800-63A</a></h3>
  <h6>Identity Proofing & Enrollment</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.ja.html"><img src="assets/800_63_3_Authenticators.png" alt="SP 800-63B" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.ja.html">SP 800-63B</a></h3>
  <h6>Authentication & Lifecycle Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.ja.html"><img src="assets/800_63_3_Federation.png" alt="SP 800-63C" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.ja.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>

NIST SP 800-63-3 Public Preview へようこそ !
本ドキュメントの大きな転換点を共有できることを嬉しく思います.
みなさんの協力を得て本ガイダンスを強化, 進化させていくとともに, 今夏には Public Draft も公開する予定です.

<!-- Welcome to the NIST SP 800-63-3 Public Preview!  We're excited to share the major transformation that this document has undergone, as well as collaboratively enhance and evolve the guidance as we head to a public draft later this summer. -->

## A few formalities

### Public preview vs public draft

みなさんがこのページにたどり着いたということは, 我々が GitHub 上でこのサイトを運営していることにお気づきでしょう.
これは "伝統的" NIST Special Publication (SP) へのコメント募集期間の運用方法とは少し異なります.
NIST 自身やその他の政府関係機関の Public Draft に関する正式な手続きとは異なるため, 我々はこの方法を Public Preview と呼んでいます.
Public Preview では, 進行中のすべてのプロセスがみなさんに公開されています.
これは我々のやり方にも変化を与えるでしょう...

<!-- If you've made it to this page, you can see we're approaching this a little differently by putting our work up on GitHub, rather than the "traditional" comment period for a NIST Special Publication (SP). We're calling it a public preview because some of our agency partners (and NIST itself) have formal processes for public drafts. Calling it a public preview is our way of letting everyone know those processes aren't in play. This lets us do things differently... -->

### A different cadence

Public Preview では, SP Draft に対する一連のオープンコメント期間と変更の繰り返しを通じて, みなさんからのインプットを集めることにフォーカスしています.
このフェーズでは, およそ2週間のコメント期間の後, 2-3週間のコメント審査およびドキュメント更新期間を複数回繰り返す予定です.

<!-- This public preview is focused on gaining input through successive open comment periods and editing iterations of the SP draft. This phase will include multiple iterations of comments of approximately 2 weeks in length, followed by a 2-3 week period for the editors to adjudicate comments and make appropriate updates to the document. -->

我々は有用なフィードバックがある限り, このイテレーションを続ける予定です.
毎イテレーションごと, もしくは日々更新を確認することを歓迎します.
基本的に大規模な更新は2-3週間おきに行われますが, それ以外でも更新を行うことはあります.

<!-- We'll continue iterations for as long as we have feedback that results in meaningful changes. We welcome you to come back every iteration to see what's new, or watch daily. While we'll be posting major iterations every few weeks, we'll also make updates mid-cycle. -->

### The first release

本ドキュメントは Stable Draft です.
この Draft は, NIST が産業界でのイノベーションや新たな脅威, 連邦デジタルサービスの発展の方向性などから学んだことを反映させたものです.
[public comment periods](http://csrc.nist.gov/groups/ST/eauthentication/sp800-63-2-comments-received-2015.pdf), [Executive Order 13681 -- Improving the Security of Consumer Financial Transactions](https://www.whitehouse.gov/the-press-office/2014/10/17/executive-order-improving-security-consumer-financial-transactions) を通じて, 我々は非常に多くのことを学びました.
NIST Pilot や NCCoE での産業界との連携など, NIST の継続的な日々の取り組みからも, フィードバックを得ることができました.

<!-- The work represented here is considered a stable draft, reflective of what NIST has learned about industry innovation, new threats, and an evolving landscape of federal digital services.  We have heard and learned so much through [public comment periods](http://csrc.nist.gov/groups/ST/eauthentication/sp800-63-2-comments-received-2015.pdf), [Executive Order 13681 -- Improving the Security of Consumer Financial Transactions](https://www.whitehouse.gov/the-press-office/2014/10/17/executive-order-improving-security-consumer-financial-transactions), [public workshops](http://csrc.nist.gov/publications/drafts/nistir-8103/nistir_8103_draft.pdf), and feedback from NIST's ongoing work such as NSTIC pilots and NCCoE industry collaborations. -->

しかしながら, 決してドキュメントが完成したわけでもなければ, 完璧な内容になっているわけでもありません.
そして, そういった状態での公開を目指していたわけでもないのです.
むしろ, 今こそ我々の方向性を明らかにすべき時だと思い, このドキュメントの公開に至ったのです.
ステークホルダーからのフィードバックが必要です.
SP 800-63 は連邦政府関係機関のみを対象としたものですが, プライベートセクターの事業者にも大きな影響を与えます.
ですから, 我々はコミュニティと一緒により早い段階でより頻繁にキーボードを叩くことで, SP 800-63 が市場の現在の状況を反映するのみならず, 将来に渡って政府サービスへの DIGITAL な認証にも一定レベルの貢献をもたらすことを期待しています.
(e-Authentication という単語を愛してやまなかったみなさん, すいません. しかし, 時代はもう2016年なのです! [訳注: なんのこっちゃ])

<!-- But this release is neither complete nor perfect--and it's not intended to be. Rather, we believe we're at a point where we've articulated the direction we're going, but need our stakeholders to comment on what we got right, what we got wrong, and what we missed all together. We know that while SP 800-63 is scoped to federal agencies only, it has material impact on our private sector partners.  So we want to put fingers to keyboard with the community earlier and more often in hopes this update to SP 800-63 not only reflects the current state of the market, but has a level of future-proofing for where DIGITAL authentication to government services is going.  (Apologies to those that loved the term e-Authentication, but it's 2016, folks!) -->

## A quick summary

本ドキュメントでの大きな変更点は以下の通りです.
なお, 詳細は各ドキュメントをご覧ください. (そう, 複数のドキュメントを!)

<!-- Here's a quick list for the biggest changes we've made, but you'll need to dig into the documents (yes, _documentS_) too: -->

1. LoA は各コンポーネントに分離されました.
2. Identity Proofing については完全に改訂されました.
3. 新たにパスワードガイダンスを追加しました.
4. 安全でない Authenticator (aka Token) についての記述を削除しました.
5. Federation に関する Requirement と Recommendation を追加しました.
6. 生体認証をより広く適用しました.
7. Privacy Requirements を追加しました. (作成中)
8. Usability Considerations を追加しました. (作成中)
9. その他もろもろ...

<!-- 1. LOA is decoupled into its component parts
2. Complete revamp of identity proofing
3. New password guidance
4. Removal of insecure authenticators (aka tokens)
5. Federation requirements and recommendations
6. Broader applicability of biometrics
7. Privacy requirements (under construction)
8. Usability considerations (under construction)
9. And many more... -->

Privacy と Usability の Chapter は現在作成中です.
それらの執筆に取り掛かる前に, 基本的な Requirement を明らかにしたいと思っています.
よってそれら2つのコンテンツはこれから数回のイテレーションを経てリリースされると期待していますし, 提案も歓迎します!

<!-- Please note that the privacy and usability chapters are under construction.  We wanted to establish a baseline set of requirements before we plunged into those sections.  Expect to see content there in the future iterations, and we welcome suggestions! -->

## Why GitHub

[訳注: 以降は GitHub を誉めたたえる文章が続きますが, SP 800-63 自体には関係ないので翻訳しません.]

Ok, "Why GitHub?" you ask. For us, the choice was relatively straightforward. GitHub has been a mainstay of the development and standards communities for many years now, serving as a space for collaborative interaction, the epicenter for evolving open source software, and an essential component in every coder’s toolkit. It only seemed appropriate for us to engage where so much of our community already congregates and collaborates.

Second, as a platform, GitHub has many unique characteristics that make it attractive as a place to develop this special publication. From its ability to support broad engagement, to excellent version control, and multiple avenues for collecting and receiving input—it is a robust forum suited to this phase of drafting the 800-63-3 suite.

Overall, GitHub is the right tool for the job. But this is a new process for us; we don't want to leave anyone out, and we anticipate some growing pains as we work this out together.

To that end, our use of GitHub is additive to the existing open and transparent process that NIST already follows. If you don't have the time this spring and summer to keep up with us, don't worry.  We will maintain our tradition of extended public comment after this process comes to a close.  

However, to manage this phase properly, we sincerely request that commenters provide substantive input.  Editorial or general comments will be accepted begrudgingly.  We want substantive technical/procedural comments.  We'll get to the grammar and formatting later. Trust us, this is as hard for some of the rather strict grammarians here at NIST as it is for anyone!

In addition, commenters are **STRONGLY** encouraged to collaborate with the team and other public participants via GitHub issues. See [this page](comment_help.html) for details on how to submit a comment to us.  We want to maintain a lean approach, so we are discouraging email and Excel files during this phase. We thank you in advance for your efforts to keep this process streamlined for the editors.

So have at it!  We're really excited about the changes we've made - we think you will be too!

Source information, current standards, and public comments received through May 2015 can be found [here](http://csrc.nist.gov/groups/ST/eauthentication/sp800-63-2_call-comments.html).

{% comment %}
<div class="text-center">
    <a href="sp800-63-3" class="btn btn-primary btn-lg" role="button">SP 800-63-3</a>
    <a href="sp800-63a" class="btn btn-primary btn-lg" role="button">SP 800-63A</a>
    <a href="sp800-63b" class="btn btn-primary btn-lg" role="button">SP 800-63B</a>
    <a href="sp800-63c" class="btn btn-primary btn-lg" role="button">SP 800-63C</a>
</div>
{% endcomment %}

<ul class="audiences">
<li>
  <div>
    <a href="sp800-63-3.ja.html"><img src="assets/800_63_3_doc.png" alt="SP 800-63-3" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63-3.ja.html">SP 800-63-3</a></h3>
  <h6>Digital Authentication Guideline</h6>
</li>
<li>
  <div>
    <a href="sp800-63a.html"><img src="assets/800_63_3_Proofing.png" alt="SP 800-63A" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63a.html">SP 800-63A</a></h3>
  <h6>Enrollment & Identity Proofing</h6>
</li>
<li>
  <div>
    <a href="sp800-63b.ja.html"><img src="assets/800_63_3_Authenticators.png" alt="SP 800-63B" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63b.ja.html">SP 800-63B</a></h3>
  <h6>Authentication & Lifecycle Management</h6>
</li>
<li>
  <div>
    <a href="sp800-63c.ja.html"><img src="assets/800_63_3_Federation.png" alt="SP 800-63C" width="150px" height="150px"></a>
  </div>
  <h3><a href="sp800-63c.ja.html">SP 800-63C</a></h3>
  <h6>Federation & Assertions</h6>
</li>
</ul>

</div>
</div>
</section>
