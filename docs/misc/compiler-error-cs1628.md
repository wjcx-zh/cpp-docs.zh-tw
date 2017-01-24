---
title: "編譯器錯誤 CS1628 | Microsoft Docs"
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
  - "CS1628"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1628"
ms.assetid: 520f864c-afe3-4db2-b44e-cfaac28ff49d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1628
無法在匿名方法、Lambda 運算式或查詢運算式內使用 ref 或 out 參數 'parameter'  
  
 如果您在匿名方法區塊內使用 ref 或 out 參數，就會發生此錯誤。 要避免這個錯誤，請使用區域變數或其他建構。  
  
 下列範例會產生 C1628：  
  
```  
// CS1628.cs delegate int MyDelegate(); class C { public static void F(ref int i) { MyDelegate d = delegate { return i; };  // CS1628 // Try this instead: // int tmp = i; // MyDelegate d = delegate { return tmp; }; } public static void Main() { } }  
```