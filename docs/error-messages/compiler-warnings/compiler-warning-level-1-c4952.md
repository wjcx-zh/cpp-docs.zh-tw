---
title: "編譯器警告 (層級 1) C4952 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4952"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4952"
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4952
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'function' : 在程式資料庫 'pgd\_file' 中找不到分析資料  
  
 使用 [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md) 時，編譯器偵測到輸入模組在 `/LTCG:PGINSTRUMENT` 之後經過重新編譯，且出現新的函式 \(**函式**\)。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 `/LTCG:PGINSTRUMENT`，並重做所有測試執行，然後執行 `/LTCG:PGOPTIMIZE`。  
  
 如果已使用 `/LTCG:PGOPTIMIZE`，則這個警告會變成錯誤。