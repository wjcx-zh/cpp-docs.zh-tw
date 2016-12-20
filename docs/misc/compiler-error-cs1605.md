---
title: "編譯器錯誤 CS1605 | Microsoft Docs"
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
  - "CS1605"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1605"
ms.assetid: a202d3a9-9777-4902-a7b9-1628640f9433
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1605
無法將 'var' 當做 ref 或 out 引數傳遞，因為它是唯讀的  
  
 必須在呼叫的方法中修改傳遞為 [ref](../Topic/ref%20\(C%23%20Reference\).md) 或 [out](../Topic/out%20\(C%23%20Reference\).md) 參數的變數。 因此，不可能將唯讀參數傳遞為 `ref` 或 `out`。