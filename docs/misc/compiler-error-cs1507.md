---
title: "編譯器錯誤 CS1507 | Microsoft Docs"
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
  - "CS1507"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1507"
ms.assetid: e1be3aba-81dc-4f65-87a4-d3f90b82dc7d
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1507
建立模組時無法連結資源檔案 'file'  
  
 [\/linkresource](../Topic/-linkresource%20\(C%23%20Compiler%20Options\).md) 已用於使用 [\/target:module](../Topic/-target:module%20\(C%23%20Compiler%20Options\).md) 進行的相同編譯，這是不允許的作業。 例如，下列選項會產生 CS1507：  
  
```  
csc /linkresource:rf.resource /target:module in.cs  
```  
  
 不過，允許內嵌資源 \([\/resource](../Topic/-resource%20\(C%23%20Compiler%20Options\).md)\)。