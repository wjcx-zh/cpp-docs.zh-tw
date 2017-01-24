---
title: "編譯器錯誤 CS1041 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1041"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1041"
ms.assetid: 9f62c058-cd28-4cb5-835c-d0f25f4fd08e
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1041
必須是識別項，'keyword' 為關鍵字  
  
 在必須是識別項的位置，找到 C\# 語言的保留字。 請將[關鍵字](../Topic/C%23%20Keywords.md)取代為使用者指定的識別項。  
  
## 範例  
 下列範例會產生 CS1041：  
  
```  
// CS1041a.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int i) { } public static void Main() { } }  
```  
  
## 範例  
 當您從沒有同一組保留字的另一種程式設計語言中匯入時，可以使用 @ 前置詞修改保留識別項 \(如下列範例所示\)。  
  
 前置詞為 `@` 的識別項稱為逐字識別項。  
  
```  
// CS1041b.cs class MyClass { public void f(int long)   // CS1041 // Try the following instead: // public void f(int @long) { } public static void Main() { } }  
```