---
title: "編譯器錯誤 CS1007 | Microsoft Docs"
ms.custom: ""
ms.date: "11/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CS1007"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1007"
ms.assetid: b56ee2c6-8e79-4b9b-8c59-194bdb22bc3e
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1007
屬性存取子已定義  
  
 當您宣告[屬性](../Topic/Using%20Properties%20\(C%23%20Programming%20Guide\).md)時，您也必須宣告其存取子方法。 不過，屬性不能有多個 `get` 存取子方法或多個 `set` 存取子方法。  
  
## 範例  
 下列範例會產生 CS1007：  
  
```  
// CS1007.cs public class clx { public int MyProperty { get { return 0; } get   // CS1007, this is the second get method { return 0; } } public static void Main() {} }  
```