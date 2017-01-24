---
title: "編譯器錯誤 CS0727 | Microsoft Docs"
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
  - "CS0727"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS0727"
ms.assetid: 54bfb87e-d759-4310-a8ab-02dccd06337c
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS0727
無效的格式規範  
  
 這個錯誤發生在偵錯工具中。 當您在其中一個偵錯工具視窗中輸入變數名稱時，可以接著依序輸入逗號和格式規範。 範例包括：myInt, h; 或 myString,nq。 編譯器完全無法剖析您輸入的內容時，就會發生這個錯誤。 若要解決此錯誤，請重新輸入變數名稱，並且選擇性地加上逗號和[有效的格式規範](../Topic/Format%20Specifiers%20in%20C%23.md)。