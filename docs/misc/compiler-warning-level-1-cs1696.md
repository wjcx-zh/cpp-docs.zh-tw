---
title: "編譯器警告 (層級 1) CS1696 | Microsoft Docs"
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
  - "CS1696"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1696"
ms.assetid: 69a45988-1aba-4a01-a84e-7ca59f8dde28
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1696
必須是單行註解或行結尾  
  
 編譯器要求前置處理器指示詞必須後接行結尾結束字元或單行註解。 編譯器已處理好有效的前置處理器指示詞，並遇到違反此語法條件約束的項目。  
  
## 範例  
 下列範例會產生 CS1696：  
  
```  
// CS1696.cs class Test { public static void Main() { #pragma warning disable 1030;219   // CS1696 #pragma warning disable 1030   // OK } }  
```