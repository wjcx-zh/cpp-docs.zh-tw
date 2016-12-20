---
title: "編譯器錯誤 CS0102 | Microsoft Docs"
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
  - "CS0102"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0102"
ms.assetid: c9419779-649f-4c24-b0f3-f0a1be46659e
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0102
類型 'type name' 已經包含 'identifier' 的定義  
  
 類別包含相同範圍內同名識別項的多個宣告。 若要修正錯誤，請重新命名重複的識別項。  
  
## 範例  
 下列範例會產生 CS0102。  
  
```  
// CS0102.cs // compile with: /target:library namespace MyApp { public class MyClass { string s = "Hello"; string s = "Goodbye";   // CS0102 public void GetString() { string s = "Hello again";   // method scope, no error } } }  
  
```