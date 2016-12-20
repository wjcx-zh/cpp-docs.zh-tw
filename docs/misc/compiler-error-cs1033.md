---
title: "編譯器錯誤 CS1033 | Microsoft Docs"
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
  - "CS1033"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1033"
ms.assetid: eb0f4001-84a6-4918-a648-cf710d038de7
caps.latest.revision: 7
caps.handback.revision: 7
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器錯誤 CS1033
原始程式檔已超過 PDB 所能顯示的上限 16,707,565 行; 偵錯資訊可能會不正確。  
  
 原始程式檔超過編譯器可處理的最大允許行數。 若要解決此錯誤，請從原始檔建立兩個或更多的原始程式碼檔。 最大行數是 268,435,454 行。 如果您使用 **\/debug**，則使用超過 16,707,566 行會導致偵錯資訊成為亂碼。