---
title: "編譯器錯誤 CS0576 | Microsoft Docs"
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
  - "CS0576"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0576"
ms.assetid: c409f8ba-4a59-48d3-9bd8-4e9053219875
caps.latest.revision: 13
caps.handback.revision: 13
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0576
命名空間 'namespace' 包含與別名 'identifier' 相衝突的定義  
  
 嘗試重複使用相同的命名空間。  
  
## 範例  
 下列範例會產生 CS0576：  
  
```  
// CS0576.cs using SysIO = System.IO; public class SysIO { public void MyMethod() {} } public class Test { public static void Main() { SysIO.Stream s;   // CS0576 } }  
```