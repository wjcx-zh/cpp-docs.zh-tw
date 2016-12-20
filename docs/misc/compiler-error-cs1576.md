---
title: "編譯器錯誤 CS1576 | Microsoft Docs"
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
  - "CS1576"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1576"
ms.assetid: 3e39cb80-e7de-4c78-a22a-57e267121a96
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1576
為 \#line 指示詞指定的行號遺漏或無效  
  
 編譯器偵測到傳遞給 [\#line](../Topic/%23line%20\(C%23%20Reference\).md) 指示詞的值發生錯誤。  
  
 下列範例會產生 CS1576：  
  
```  
// CS1576.cs public class MyClass { static void Main() { #line "abc.sc"         // CS1576 // try the following line instead //#line  101 "abc.sc" intt i;  // error will be reported on line 101 } }  
```