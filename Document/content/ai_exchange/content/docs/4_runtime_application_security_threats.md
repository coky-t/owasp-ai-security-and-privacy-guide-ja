---
title: 4. 実行時の従来のセキュリティ脅威
heroTitle: "実行時の従来のセキュリティ脅威"
heroText: "入力攻撃とは別の、運用中の AI システムへの攻撃と保護コントロール"
weight: 5
---
> カテゴリ: 実行時脅威のグループ  
> パーマリンク: https://owaspai.org/go/runtimeconventionalsec/

AI システムは IT システムであるため、実行時にはあらゆるセキュリティ攻撃に脆弱となる可能性があります。たとえば、アプリケーションのユーザーデータベースへの侵入があります。これらの一般的な資産への「従来型」攻撃とその対抗策は他の多くのリソースでカバーされます。このセクションでは AI 特有のものについてのみ焦点を当てています。

[セクション 2](2_threats_through_use.md) は AI 特有の実行時攻撃をカバーします。推論時に実行される攻撃であり、システムを使用したり、モデル入力を提供します。[セクション 3](3_development_time_threats.md) は開発時の攻撃をカバーします。主に従来型の攻撃 (トレーニングデータベースへの侵入など) ですが AI 特有の結果 (モデル挙動の変化など) や AI 特有のサプライチェーン攻撃があります。

そのため、このページでは、AI 特有の結果を持つ従来型のセキュリティ攻撃をカバーします。たとえば、拡張データ (モデル入力に追加されるデータ) のランタイムデータベースに不正侵入することでモデル挙動を変更するものです。これらの攻撃の詳細な実行方法は他の多くのリソースでカバーされています。このセクションでは AI 特有の結果と、必要とされるコントロールのカテゴリに焦点を当てています。従来の攻撃に対するコントロールの詳細については他の多くのリソースでカバーされています。このセクションでは、モデルに対して Trusted Execution Environment を使用するというオプションなど、これらのコントロールの AI 特有の側面に焦点を当てています。

サブセクションでは、AI 特有ではない脅威、モデルポイズニング、モデル漏洩、安全でない出力処理、入力データの漏洩、拡張データへの攻撃をカバーします。

## 4.1. 一般的なセキュリティ脅威
> カテゴリ: 実行時脅威のグループ  
> パーマリンク: https://owaspai.org/go/genericsecthreats/

**Description**  
Impact: Conventional security threats can impact confidentiality, integrity and availability of all assets.

AI systems are IT systems and therefore can have security weaknesses and vulnerabilities that are not AI-specific such as SQL-Injection. Such topics are covered in depth by many sources and are out of scope for this publication.  
Note: some controls in this document are conventional security controls that are not AI-specific, but applied to AI-specific threats (e.g., monitoring to detect model attacks).

**Controls**

- See the [Governance controls](/go/governancecontrols/) in the general section, in particular [SECDEVPROGRAM](/go/secdevprogram/) to attain application security, and [SECPROGRAM](/go/secprogram/) to attain information security in the organization.
- Technical conventional security controls  
  Useful standards include:
  - See [OpenCRE on technical conventional security controls](https://www.opencre.org/cre/636-660)
  - The ISO 27002 controls only partly cover technical conventional security controls, and on a high abstraction level
  - More detailed and comprehensive control overviews can be found in for example, Common criteria protection profiles (ISO/IEC 15408 with evaluation described in ISO 18045),
  - or in [OWASP ASVS](https://owasp.org/www-project-application-security-verification-standard/)
- Operational security  
  When models are hosted by third parties then security configuration of those services deserves special attention. Part of this configuration is [model access control](/go/modelaccesscontrol/):  an important mitigation for security risks. Cloud AI configuration options deserve scrutiny, like for example opting out when necessary of monitoring by the third party - which could increase the risk of exposing sensitive data.
  Useful standards include:
  - See [OpenCRE on operational security processes](https://www.opencre.org/cre/862-452)
  - The ISO 27002 controls only partly cover operational security controls, and on a high abstraction level

---

## 4.2. 直接的な実行時モデルポイズニング
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/runtimemodelpoison/

**Description**  
Impact: see Broad model poisoning.

This threat involves manipulating the behavior of the model by altering the parameters within the live system itself. These parameters represent the regularities extracted during the training process for the model to use in its task, such as neural network weights. Alternatively, compromising the model's input or output logic can also change its behavior or deny its service.

**Controls**  

- See [General controls](/go/generalcontrols/)
- The below control(s), each marked with a # and a short name in capitals

#### #RUNTIME MODEL INTEGRITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/runtimemodelintegrity/

**Description**  
Run-time model integrity: apply traditional conventional security controls to protect the storage of model parameters (e.g., access control, checksums, encryption) A Trusted Execution Environment can help to protect model integrity.

#### #RUNTIME MODEL IO INTEGRITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/runtimemodeliointegrity/

**Description**  
Run-time model Input/Output integrity: apply conventional security controls to protect the runtime manipulation of the model's input/output logic (e.g., protect against a man-in-the-middle attack)

---

## 4.3. 直接的な実行時モデル漏洩
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/runtimemodelleak/

**Description**  
Impact:  Confidentiality breach of the model (i.e., model parameters), which can be:
- intellectual property theft (e.g., by a competitor)
- and/or a way to perform input attacks on the copied model, circumventing protections. These protections include rate limiting, access control, and detection mechanisms. This can be done for [all input attacks](/go/inputthreats/) that extract data, and for the preparation of [evasion](/go/evasion/) or [prompt injection](/go/promptinjection/): experimenting to find attack inputs that work.
 
This attack occurs when stealing model parameters from a live system by breaking into it (e.g., by gaining access to executables, memory or other storage/transfer of  parameter data in the production environment). This is different from [model exfiltration](/go/modelexfiltration/) which goes through a number of steps to steal a model through normal use, hence the use of the word 'direct'. It is also different from [direct development-time model leak](/go/devmodelleak/) from a lifecycle and attack surface perspective.

This attack also includes _side-channel attacks_, where attackers do not necessarily steal the entire model but instead extract specific details about the model’s behaviour or internal state. By observing characteristics like response times, power consumption, or electromagnetic emissions during inference, attackers can infer sensitive information about the model. This type of attack can provide insights into the model's structure, the type of data it processes, or even specific parameter values, which may be leveraged for subsequent attacks or to replicate the model.


**Risk identification**  
This threat applies if the model represents intellectual property (i.e., a trade secret), or the risk of any input attack applies - with the exception of the model being publicly available because then there is no need to steal it.

**Controls**

- [General controls](/go/generalcontrols/),
  - especially [Sensitive data limitation](/go/dataminimize/)
- [#MODEL WATERMARKING](/go/modelwatermarking/)
- The below control(s), each marked with a # and a short name in capitals
  
#### #RUNTIME MODEL CONFIDENTIALITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/runtimemodelconfidentiality/

**Description**  
Run-time model confidentiality: see [SECDEVPROGRAM](/go/secdevprogram/) to attain conventional security, with the focus on protecting the storage of model parameters (e.g., access control, encryption).  

A Trusted Execution Environment can be highly effective in safeguarding the runtime environment, isolating model operations from potential threats, including side-channel hardware attacks like [DeepSniffer](https://sites.cs.ucsb.edu/~sherwood/pubs/ASPLOS-20-deepsniff.pdf). By ensuring that sensitive computations occur within this secure enclave,the TEE reduces the risk of attackers gaining useful information through side-channel methods.

Side-Channel Mitigation Techniques:
- Masking: Introducing random delays or noise during inference can help obscure the relationship between input data and the model’s response times, thereby complicating timing-based side-channel attacks. See [Masking against Side-Channel Attacks: A Formal Security Proof](https://www.iacr.org/archive/eurocrypt2013/78810139/78810139.pdf)

- Shielding: Employing hardware-based shielding could help prevent electromagnetic
or acoustic leakage that might be exploited for side-channel attacks. See [Electromagnetic Shielding for Side-Channel Attack Countermeasures](https://ieeexplore.ieee.org/document/8015660)


#### #MODEL OBFUSCATION
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/modelobfuscation/

**Description**  
Model obfuscation: techniques to store the model in a complex and confusing way with minimal technical information, to make it more difficult for attackers to extract and understand a model after having gained access to its runtime storage. See this [article on ModelObfuscator](https://dl.acm.org/doi/abs/10.1145/3597926.3598113)

---

## 4.4. 従来のインジェクションを含む出力
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/outputcontainsconventionalinjection/

**Description**  
Impact: Textual model output may contain conventional injection attacks such as XSS-Cross site scripting, which can create a vulnerability when processed (e.g., shown on a website, execute a command).

This is like the standard output encoding issue, but the particularity is that the output of AI may include attacks such as XSS.

A special form of this threat is when it is used to exfiltrate data, for example when a model is manipulated to output javascript code that is executed and sends sensitive data to a third party. 

A special sub form of exfiltrating to third parties through output is when sensitive data is packed into URLs in the output - for users to click on, or images to retrieve. According to classic definitions this is not injection, but the spirit of the mechanism is and therefore it is in scope of this threat: data gets 'executed' by a web request (http): either by an image being rendered in a browser, or a user clicking on a link.

**References**  
<!-- OPENCRE_SECTION_CRE_START slug=outputcontainsconventionalinjection -->
- [OpenCRE: Model output contains conventional injection](https://opencre.org/cre/780-757)
    referring to:
    - [OWASP Top10 for LLM: sec. LLM05:2025: Improper Output Handling](https://genai.owasp.org/llmrisk/llm052025-improper-output-handling/)
    - [MITRE ATLAS: sec. AML.T0051: LLM Prompt Injection](https://atlas.mitre.org/techniques/AML.T0051)
<!-- OPENCRE_SECTION_CRE_END slug=outputcontainsconventionalinjection -->
See [OWASP for LLM 05](https://genai.owasp.org/llmrisk/llm05/).

**Controls:**

- The below control(s), each marked with a # and a short name in capitals

#### #ENCODE MODEL OUTPUT
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/encodemodeloutput/

**Description**  
Encode model output: apply output encoding on model output if it's text. See [OpenCRE on Output encoding and injection prevention](https://www.opencre.org/cre/161-451)

---

## 4.5. 入力データ漏洩
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/inputdataleak/

**Description**  
Impact: Confidentiality breach of sensitive input data through a conventional attack on the data at rest or in transit.

Input data (e.g., GenAI prompts) can be sensitiv and can either leak through a failure or through an attack, such as a man-in-the-middle attack.  

The following factors can complicate this risk:
1. Metadat. If there is metadata to the input (e.g., identifying a user), this can increase the risk - for example when a sensitive conversation in prompts is linked to the user.
2. Cloud AI. When AI models run in the cloud (often the case for GenAI) then this risk needs special attention, especially if this is managed by an external party. Uput data will be unencrypted at inference time (when processed by the model). Therefore, it is critical that proper security measures are in place for the data in transit and at rest, and ideally the data is not retained at all. For security reasons, some third parties monitor and log the input, which is why it is critical to read the fine print and select the right license and configuration. Sometimes monitoring requires opt-out.
3. Court orders. If input is stored at the third party, you run the risk of that data to be subject to a subpoena. 
4. Agumented data. GenAI model input (prompts) can contain rich context information with sensitive data (e.g., company secrets). The latter issue occurs with *in context learning* or *Retrieval Augmented Generation(RAG)* (adding background information to a prompt): for example data from all reports ever written at a consultancy firm. First of all, this context information will travel with the prompt to the cloud, and second: the context information may likely leak to the output, so it's important to apply the access rights of the user to the retrieval of the context. For example: if a user from department X asks a question to an LLM - it should not retrieve context that department X has no access to, because that information may leak in the output.
5. External services. Model actions may trigger other services, further spreading the input data. For example: when you ask a cloud AI to process your pdf document and the AI starts calling various services to help process the document. 

See [Risk analysis](https://owaspai.org/docs/ai_security_overview/#how-to-select-relevant-threats-and-controls-risk-analysis) on responsible parties.

**Controls**
- See [General controls](/go/generalcontrols/), in particular [Minimizing data](/go/datalimit/)
- The below control(s), each marked with a # and a short name in capitals

#### #MODEL INPUT CONFIDENTIALITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/modelinputconfidentiality/

**Description**  
Model input confidentiality: see [SECDEVPROGRAM](/go/secdevprogram/) to attain conventional security, with the focus on protecting the transport and storage of model input (e.g., access control, encryption, minimize retention)

---

## 4.6. 直接的な拡張データ漏洩
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/augmentationdataleak/

**Description**  
Impact: Confidentiality breach of sensitive augmentation data through a conventional attack on the data at rest or in transit.

Augmentation data (ad hoc retrieved information inserted into a prompt, such as system prompts, or documents), needs to be transfered and stored - for example for Retrieval Augmented Generation typically in _vector databases_. This increases the attack surface for any sensitive data, since it's stored outside its regular storage with the regular protection (e.g., company document archive) and therefore requires additional protection.   

So-called _vectors_ that form a representation of augmentation data are typically vulnerable for extracting information and should therefore be included in protection.

Alternative ways for augmentation data to leak are:
- [input data leak](/go/inputdataleak/)
- [disclosure in output](/go/disclosureinoutput/) - it is best to assume that augmentation data can leak to the output, so the access rights for that data need to align with the rights of the user(s) that can see the output. 

**References**
<!-- OPENCRE_SECTION_CRE_START slug=augmentationdataleak -->
- [OpenCRE: Augmentation data leak](https://opencre.org/cre/173-554)
    referring to:
    - [MITRE ATLAS: sec. AML.T0036: Data from Information Repositories](https://atlas.mitre.org/techniques/AML.T0036)
    - [NIST AI 100-2: sec. 3.2.2: Poisoning Attacks](https://csrc.nist.gov/pubs/ai/100/2/e2023/final)
<!-- OPENCRE_SECTION_CRE_END slug=augmentationdataleak -->
- [Mitigating Security Risks in RAG LLM Applications, November 2023, CSA](https://cloudsecurityalliance.org/blog/2023/11/22/mitigating-security-risks-in-retrieval-augmented-generation-rag-llm-applications)

**Controls**
- See [General controls](/go/generalcontrols/)
- The below control(s), each marked with a # and a short name in capitals

#### #AUGMENTATION DATA CONFIDENTIALITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/augmentationdataconfidentiality/

**Description**  
See the [security program](/go/secprogram/) and [application security](/go/secdevprogram/), [development environment security](/go/devsecurity/), and [data segregation](/go/segregatedata/) to protect the confidentiality of transporting and storing augmentation data (e.g., access control, encryption, minimize retention).



---

## 4.7. 拡張データ操作
> Category: runtime conventional security threat  
> パーマリンク: https://owaspai.org/go/augmentationdatamanipulation/

**Description**  

Impact: Integrity breach of augmentation data through a conventional attack on the data at rest or in transit - leading to manipulated model behaviour.

Augmentation data (context information added to a prompt) can be stored in for example _vector databases_, _system prompt storage_, or the working memory of an agent. When augmentation data is manipulated (e.g., inserting false information), it can change the behaviour of the model - making it very similar to [data poisoning](/go/datapoison/).

**References**
<!-- OPENCRE_SECTION_CRE_START slug=augmentationdatamanipulation -->
- [OpenCRE: Augmentation data manipulation](https://opencre.org/cre/217-163)
    referring to:
    - [MITRE ATLAS: sec. AML.T0070: RAG Poisoning](https://atlas.mitre.org/techniques/AML.T0070)
    - [NIST AI 100-2: sec. 3.4.2: Integrity Violations](https://csrc.nist.gov/pubs/ai/100/2/e2023/final)
<!-- OPENCRE_SECTION_CRE_END slug=augmentationdatamanipulation -->
- [Mitigating Security Risks in RAG LLM Applications, November 2023, CSA](https://cloudsecurityalliance.org/blog/2023/11/22/mitigating-security-risks-in-retrieval-augmented-generation-rag-llm-applications)

**Controls**
- See [General controls](/go/generalcontrols/)
- The below control(s), each marked with a # and a short name in capitals

#### #AUGMENTATION DATA INTEGRITY
> Category: runtime information security control against conventional security threats  
> パーマリンク: https://owaspai.org/go/augmentationdataintegrity/

**Description**  
See the [security program](/go/secprogram/) and [application security](/go/secdevprogram/), [development environment security](/go/devsecurity/), and [data segregation](/go/segregatedata/) to protect the integrity of transporting and storing augmentation data (e.g., access control, encryption, minimize retention).
