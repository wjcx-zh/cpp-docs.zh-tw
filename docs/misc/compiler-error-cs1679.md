---
title: "編譯器錯誤 CS1679 | Microsoft Docs"
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
  - "CS1679"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1679"
ms.assetid: c42e9bca-212a-458e-88f8-b81c812436bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1679
無效的 '\/reference' 外部別名; 'identifier' 不是有效的識別項  
  
 根據 C\# 語言規格，使用 **\/reference** 選項的外部組件別名功能時，**\/reference:** 之後及 '\=' 之前的文字必須是有效的 C\# 識別項或關鍵字。  
  
 若要更正這個錯誤，請將 "\=" 之前的文字變更為有效的 C\# 識別項或關鍵字。  
  
## 範例  
 下列範例會產生 CS1679。  
  
```  
// CS1679.cs // compile with: /reference:123$BadIdentifier%=System.dll class TestClass { static void Main() { } }  
```