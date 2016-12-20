---
title: "編譯器錯誤 CS1661 | Microsoft Docs"
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
  - "CS1661"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1661"
ms.assetid: 162d5736-ca3c-4a09-a5d9-a19da3d5bf24
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1661
無法將匿名方法區塊轉換為委派類型 'delegate type'，因為指定區塊的參數類型不符合委派參數類型  
  
 如果在匿名方法定義中，匿名方法的參數類型不符合委派參數類型，就會發生這個錯誤。 請檢查參數個數、參數類型，以及任何 ref 或 out 參數，並確認完全相符。  
  
 下列範例會產生 CS1661：  
  
```  
// CS1661.cs delegate void MyDelegate(int i); class C { public static void Main() { MyDelegate d = delegate(string s) { };  // CS1661 } }  
```