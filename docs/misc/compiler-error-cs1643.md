---
title: "編譯器錯誤 CS1643 | Microsoft Docs"
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
  - "CS1643"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1643"
ms.assetid: 521f352b-00fb-4d62-89be-44251db3cc5b
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1643
部分程式碼路徑並未傳回類型 'type\!' 的方法中的值  
  
 如果委派主體沒有 return 陳述式，或具有編譯器無法驗證將達到的 return 陳述式，就會發生這個錯誤。 在下列範例中，編譯器不會嘗試預測分支條件的結果，以確認匿名方法區塊一律會傳回值。  
  
## 範例  
 下列範例會產生 CS1643：  
  
```  
// CS1643.cs delegate int MyDelegate(); class C { static void Main() { MyDelegate d = delegate {                 // CS1643 int i = 0; if (i == 0) return 1; }; } }  
```