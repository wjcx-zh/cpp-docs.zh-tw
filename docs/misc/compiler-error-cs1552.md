---
title: "編譯器錯誤 CS1552 | Microsoft Docs"
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
  - "CS1552"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1552"
ms.assetid: 647af14d-249e-4f69-80a8-2c0d77fbb244
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1552
陣列類型規範 \[\] 必須出現在參數名稱之前  
  
 陣列類型規範的位置在陣列宣告的變數名稱後面。  
  
## 範例  
 下列範例會產生 CS1552：  
  
```  
// CS1552.cs public class C { public static void Main(string args[])   // CS1552 // try the following line instead // public static void Main(string [] args) { } }  
```