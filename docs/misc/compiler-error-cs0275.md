---
title: "編譯器錯誤 CS0275 | Microsoft Docs"
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
  - "CS0275"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0275"
ms.assetid: 4d59f11c-b0ea-4c91-b2cb-cbe3be9a9ba2
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0275
'accessor': 存取範圍修飾詞不可使用於介面的存取子上  
  
 當您對屬性或介面中索引子的任何一個存取子使用存取修飾詞，就會發生此錯誤。 若要解決，請移除存取修飾詞。  
  
## 範例  
 下列範例會產生 CS0275：  
  
```  
// CS0275.cs public interface MyInterface { int Property { get; internal set;   // CS0275 } }  
```