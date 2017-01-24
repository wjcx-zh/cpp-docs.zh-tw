---
title: "疑難排解例外狀況：System.IdentityModel.Selectors.PolicyValidationException | Microsoft Docs"
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
  - "PolicyValidationException 例外狀況"
  - "System.IdentityModel.Selectors.PolicyValidationException 例外狀況"
ms.assetid: 510c7698-a12b-4bcb-a9d8-87c704b62ffa
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.IdentityModel.Selectors.PolicyValidationException
當收件者所提供的原則無法驗證時，就會擲回 <xref:System.IdentityModel.Selectors.PolicyValidationException> 例外狀況 \(Exception\)。 如需原則需求的詳細資訊，請參閱 [Information Card Profile V1.0 技術參考](http://go.microsoft.com/fwlink/?LinkID=102401)。  
  
 任何無效的原則內容都可能導致這個失敗。 與原則內容有關的常見問題包含下列各項：  
  
-   無效的金鑰類型  
  
-   無效的金鑰大小  
  
-   無效的 XML  
  
-   原則內未指定任何宣告 \(至少必須指定一項非選擇性的宣告\)  
  
## 請參閱  
 <xref:System.IdentityModel.Selectors.PolicyValidationException>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)