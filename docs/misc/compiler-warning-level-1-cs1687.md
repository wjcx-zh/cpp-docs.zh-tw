---
title: "編譯器警告 (層級 1) CS1687 | Microsoft Docs"
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
  - "CS1687"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "CS1687"
ms.assetid: f65d184f-fa1d-45d7-be7d-f439f67bace4
caps.latest.revision: 8
caps.handback.revision: 8
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 編譯器警告 (層級 1) CS1687
原始程式檔已超過 PDB 所能顯示的上限 16,707,565 行；偵錯資訊可能會不正確  
  
 PDB 和偵錯工具有一些與檔案大小相關的限制。 如果原始程式檔太大，超過該限制的偵錯工具將無法正常運作。 使用者應該不發出該檔案的偵錯資訊，像是使用 `#line hidden`，或者尋找壓縮檔案的方式，像是將檔案分割成多個檔案。 使用者可能想要使用 `partial` 關鍵字來分割大型類別。