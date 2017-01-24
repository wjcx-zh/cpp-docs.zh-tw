---
title: "編譯器警告 (層級 4) CS0078 | Microsoft Docs"
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
  - "CS0078"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0078"
ms.assetid: 8d637be6-82bc-462c-bec5-217327bc8c40
caps.latest.revision: 6
caps.handback.revision: 6
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 4) CS0078
字尾 'l' 很容易與數字 '1' 混淆 \-\- 請使用 'L' 以避免困擾  
  
 當編譯器偵測到 long 轉換使用小寫 l 而不是大寫 L 時，就會發出警告。  
  
 下列範例會產生 CS0078：  
  
```  
// CS0078.cs // compile with: /W:4 class test { public static void TestL(long i) { } public static void TestL(int i) { } public static void Main() { TestL(25l);   // CS0078 // try the following line instead // TestL(25L); } }  
```