---
title: "編譯器警告 (層級 1) C4951 | Microsoft Docs"
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
  - "C4951"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4951"
ms.assetid: 669d8bb7-5efa-4ba9-99db-4e65addbf054
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 編譯器警告 (層級 1) C4951
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

由於已收集設定檔資料，因此 'function' 已編輯，但未使用函式設定檔資料  
  
 已將輸入模組中的函式編輯為 [\/LTCG:PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)，因此現在您的設定檔資料無效。 輸入模組在 **\/LTCG:PGINSTRUMENT** 之後已重新編譯，且相較於 **\/LTCG:PGINSTRUMENT** 作業當時模組中的控制流程，輸入模組的函式 \(***function***\) 的控制流程不同。  
  
 這個警告僅供參考。 若要解決這個警告，請執行 **\/LTCG:PGINSTRUMENT**，再取消復原所有測試回合，並執行 **\/LTCG:PGOPTIMIZE**。  
  
 如果已使用 **\/LTCG:PGOPTIMIZE**，則這個警告會變成錯誤。