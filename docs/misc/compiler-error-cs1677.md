---
title: "編譯器錯誤 CS1677 | Microsoft Docs"
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
  - "CS1677"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1677"
ms.assetid: 8c974669-15c6-4010-8b02-21021bed5af9
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1677
參數 'number' 不可以 'keyword' 關鍵字宣告  
  
 當匿名方法中的參數類型修飾詞不符合轉換方法的目標委派宣告中所使用的修飾詞時，就會發生這個錯誤。  
  
## 範例  
 下列範例會產生 CS1677：  
  
```  
// CS1677.cs delegate void D(int i); class Errors { static void Main() { D d = delegate(out int i) { };   // CS1677 // To resolve, use the following line instead: // D d = delegate(int i) { }; D d = delegate(ref int j){}; // CS1677 // To resolve, use the following line instead: // D d = delegate(int j){}; } }  
```