---
title: "疑難排解例外狀況：System.Security.VerificationException | Microsoft Docs"
ms.custom: ""
ms.date: "10/29/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "EHVerification"
dev_langs: 
  - "JScript"
  - "VB"
  - "CSharp"
  - "C++"
helpviewer_keywords: 
  - "VerificationException 類別"
ms.assetid: b7b1a4c2-6769-46bd-8912-ebbfe226bfb3
caps.latest.revision: 15
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "douge"
---
# 疑難排解例外狀況：System.Security.VerificationException
當安全性原則要求程式碼必須是型別安全，但驗證程序無法驗證該程式碼為型別安全時，就會擲回 <xref:System.Security.VerificationException> 例外狀況。  
  
## 相關秘訣  
 請確定應用程式沒有載入兩個衝突的類別庫 \(Class Library\) 版本。  
 在驗證程序中，有一部分是檢查 MSIL \(Microsoft Intermediate Language\)，藉以確定物件彼此之間互相安全的隔離，不會遭受意外或人為惡意損毀。 如需詳細資訊，請參閱[類型安全和安全性](http://msdn.microsoft.com/zh-tw/095cd1f6-d8db-4c0e-bce2-83ccb34dd5dc)。  
  
## 請參閱  
 <xref:System.Security.VerificationException>   
 <xref:System.Security.Permissions.SecurityPermissionAttribute.SkipVerification%2A>   
 [Use the Exception Assistant](../Topic/How%20to:%20Use%20the%20Exception%20Assistant.md)