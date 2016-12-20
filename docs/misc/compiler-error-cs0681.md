---
title: "編譯器錯誤 CS0681 | Microsoft Docs"
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
  - "CS0681"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0681"
ms.assetid: aa51ad94-df0a-481d-aaea-5b4291ebc41c
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0681
修飾詞 'abstract' 在欄位上無效。 請嘗試改用屬性  
  
 無法將欄位設為抽象。 不過，您可以讓抽象屬性存取欄位。  
  
## 範例  
 下列範例會產生 CS0681：  
  
```  
// CS0681.cs // compile with: /target:library abstract class C { abstract int num;  // CS0681 }  
  
```  
  
## 範例  
 請改嘗試下列程式碼：  
  
```  
// CS0681b.cs // compile with: /target:library abstract class C { public abstract int num { get; set; } }  
```