---
title: "編譯器錯誤 CS0145 | Microsoft Docs"
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
  - "CS0145"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0145"
ms.assetid: e5f9a90f-1700-4e6a-8f82-23d0c0287b85
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0145
需要為 const 欄位提供值  
  
 您必須初始化 [const](../Topic/const%20\(C%23%20Reference\).md) 變數。 如需詳細資訊，請參閱[常數](../Topic/Constants%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0145：  
  
```  
// CS0145.cs class MyClass { const int i;   // CS0145 // try the following line instead // const int i = 0; public static void Main() { } }  
```