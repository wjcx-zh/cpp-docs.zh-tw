---
title: "編譯器錯誤 CS0726 | Microsoft Docs"
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
  - "CS0726"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0726"
ms.assetid: 9ea5f004-cf25-4e6e-b9e5-6b53e4a7e1ab
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0726
'format specifier' 不是有效的格式規範  
  
 這個錯誤發生在偵錯工具中。 當您在其中一個偵錯工具視窗中輸入變數名稱時，可以接著依序輸入逗號和格式規範。 例如，`myInt, h` 和 `myString,nq`。 編譯器無法辨識[C\# 中的格式規範](../Topic/Format%20Specifiers%20in%20C%23.md)時，會發生這個錯誤。