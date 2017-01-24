---
title: "編譯器錯誤 CS1632 | Microsoft Docs"
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
  - "CS1632"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1632"
ms.assetid: fa18061a-8c6c-4788-b74e-62bacb16aed8
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1632
程式控制權不能從匿名方法或 Lambda 運算式的主體離開  
  
 如果跳躍陳述式 \(**break**、`goto`、**continue** 等\) 嘗試將控制項移出匿名方法區塊，就會發生這個錯誤。 匿名方法區塊是函式主體，只能透過傳回陳述式或到達區塊結尾來結束。  
  
 下列範例會產生 CS1632：  
  
```  
// CS1632.cs // compile with: /target:library delegate void MyDelegate(); class MyClass { public void Test() { for (int i = 0 ; i < 5 ; i++) { MyDelegate d = delegate { break;   // CS1632 }; } } }  
```