---
title: "編譯器警告 (層級 1) C4953 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4953"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4953"
ms.assetid: 3c4f6ac6-3976-41ab-8a27-3c41d7472ea7
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 編譯器警告 (層級 1) C4953
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

已經編輯內嵌項 'function'，因為已收集分析資料，未使用分析資料  
  
 使用 [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md) 時，編譯器在 `/LTCG:PGINSTRUMENT` 後面偵測到重新編譯過的輸入模組，並且具有編輯過的函式 \(***function***\)，在其中，現有測試執行會將函式視為進行內嵌的候選項目。 不過，重新編譯模組之後，函式就不再是進行內嵌的候選項目。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE`，則這個警告會變成錯誤。