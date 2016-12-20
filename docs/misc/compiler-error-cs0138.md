---
title: "編譯器錯誤 CS0138 | Microsoft Docs"
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
  - "CS0138"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0138"
ms.assetid: 970545f8-5ee5-428e-921a-3aa29f68d16d
caps.latest.revision: 9
caps.handback.revision: 9
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0138
using 命名空間指示詞只能套用到命名空間；'type' 是類型，不是命名空間  
  
 [using](../Topic/using%20\(C%23%20Reference\).md) 指示詞只可將命名空間的名稱作為參數。 如需詳細資訊，請參閱[命名空間](../Topic/Namespaces%20\(C%23%20Programming%20Guide\).md)。  
  
 下列範例會產生 CS0138：  
  
```  
// CS0138.cs using System.Object;   // CS0138  
```