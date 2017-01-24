---
title: "編譯器錯誤 CS2005 | Microsoft Docs"
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
  - "CS2005"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS2005"
ms.assetid: 03535d2a-ae30-4272-ab45-e277df5ee8e1
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS2005
遺漏 'option' 選項的檔案規格  
  
 僅能部分指定[編譯器選項](../Topic/C%23%20Compiler%20Options.md)。  
  
 例如，使用 [\/recurse](../Topic/-recurse%20\(C%23%20Compiler%20Options\).md) 時，您必須指定要搜尋的檔案：**\/recurse:**檔案名稱**.cs**。  
  
## 範例  
 下列範例會產生 CS2005。  
  
```  
// CS2005.cs // compile with: /recurse: // CS2005 expected class x { public static void Main() {} }  
```