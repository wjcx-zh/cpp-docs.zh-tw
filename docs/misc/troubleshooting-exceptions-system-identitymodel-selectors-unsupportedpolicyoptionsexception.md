---
title: "疑難排解例外狀況：System.IdentityModel.Selectors.UnsupportedPolicyOptionsException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "System.IdentityModel.Selectors.UnsupportedPolicyOptionsException 例外狀況"
  - "UnsupportedPolicyOptionsException 例外狀況"
ms.assetid: 1151127d-81a1-4d87-8462-924ab9d1ee01
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IdentityModel.Selectors.UnsupportedPolicyOptionsException
<xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException> 例外狀況 \(Exception\) 表示提供給系統的原則中包含不支援的選項。 可能導致這些失敗的限制包括下列各項：  
  
 收件者已指定 http:\/\/schemas.xmlsoap.org\/ws\/2005\/05\/identity\/issuer\/self 做為權杖 \(Token\) 的簽發者，向本機安全性權杖服務要求權杖。 不過，CardSpace 本機安全性權杖服務不支援其中一項指定於原則中的需求。 如需詳細資訊，請參閱 [Information Card Profile V1.0 技術參考](http://go.microsoft.com/fwlink/?LinkId=102401)。 不支援選項的範例包括下列各項：  
  
-   收件者所要求的宣告不會列於＜Information Card Profile V1.0 技術參考＞的[支援的宣告類型](http://go.microsoft.com/fwlink/?LinkId=102402)一節中指定的支援宣告清單。  
  
-   權杖類型並不是 SAML 1.0 或 1.1。  
  
-   非 SSL 網站的金鑰不是對稱式。  
  
-   KeyWrapAlgorithm 與預設的演算法不同。  
  
-   原則內指定了不支援的項目。 下列是支援的項目：  
  
    -   EncryptionAlgorithm  
  
    -   CanonicalizationAlgorithm  
  
    -   SignWith  
  
    -   TokenType  
  
    -   ClaimsElement  
  
    -   KeyType  
  
    -   KeySize  
  
    -   EncryptWith  
  
    -   RequestType  
  
    -   SecondaryParameters  
  
    -   KeyWrapAlgorithm  
  
-   wst:RequestType 不是 Issue 型別。  
  
-   非對稱金鑰類型的金鑰大小不是 2048。  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.UnsupportedPolicyOptionsException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)