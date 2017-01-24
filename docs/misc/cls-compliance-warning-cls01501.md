---
title: "CLS 符合性警告 CLS01501 | Microsoft Docs"
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
  - "CLS01501"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CLS01501"
ms.assetid: 74361331-3773-48d5-8508-0113f5464a75
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "douge"
---
# CLS 符合性警告 CLS01501
**varargs 條件約束不是 CLS 的一部分**  
  
 varargs 條件約束不是 Common Language Subset \(CLS\) 的一部分。  CLS 所支援的唯一呼叫慣例是標準 Managed 呼叫慣例。  
  
 如需 CLS 符合性檢查的詳細資訊，請參閱[符合 CLS 標準的組件](http://msdn.microsoft.com/zh-tw/3320b57e-ea55-4697-a17d-f509a36a3c93)。  
  
 下列函式宣告 \(使用 MSIL 組件語言\) 顯示何種狀況可能導致 CLS01501：  
  
```  
.method public specialname rtspecialname instance vararg void  .ctor() cil managed  
```  
  
 您可以使用參數陣列解決 CLS01501 錯誤。  如需詳細資訊，請參閱[Variable Argument Lists \(...\) \(C\+\+\/CLI\)](../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md)。