---
title: "編譯器錯誤 CS0117 | Microsoft Docs"
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
  - "CS0117"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0117"
ms.assetid: 2cbc7e66-75d6-4817-85ae-89c4b9adfded
caps.latest.revision: 15
caps.handback.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0117
'type' 不包含 'identifier' 的定義  
  
-   在某些情況下，當參考到資料類型沒有的成員時，就會發生這個錯誤。  
  
## 範例  
 下列範例會產生 CS0117：  
  
```  
// CS0117.cs public class BaseClass { } public class base021 : BaseClass { public void TestInt() { int i = base.someMember; //CS0117 } public static int Main() { return 1; } }  
```