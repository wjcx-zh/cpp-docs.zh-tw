---
title: "編譯器錯誤 CS1010 | Microsoft Docs"
ms.custom: ""
ms.date: "11/17/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1010"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1010"
ms.assetid: 3d47277a-253f-464b-a603-e3b37e0e7b0d
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1010
常數中包含新行字元  
  
 未適當地分隔 [string](../Topic/string%20\(C%23%20Reference\).md)。  
  
 下列範例會產生 CS1010：  
  
```  
// CS1010.cs class Sample { static void Main() { string a = "Hello World;   // CS1010 // Use the following line, with end quote before semicolon: string a = "Hello World"; // } }  
```  
  
## 請參閱  
 [NIB \- 字串 \(C\# 程式設計手冊\)](http://msdn.microsoft.com/zh-tw/1a32b1c9-0d99-468a-9734-e3a47f2e897a)