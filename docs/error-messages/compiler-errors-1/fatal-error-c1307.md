---
title: "嚴重錯誤 C1307 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1307"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1307"
ms.assetid: 6f77d3d4-ba8a-476c-b540-aff19eb4efc4
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 嚴重錯誤 C1307
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在收集分析資料時已對程式進行編輯  
  
 使用 [\/LTCG:PGOPTIMIZE](../../build/reference/ltcg-link-time-code-generation.md) 時，連結器偵測到在 \/LTCG:PGINSTRUMENT 之後已重新編譯的輸入模組，而且該模組的變更已使得現有分析資料不再相關。  例如，如果呼叫圖形在重新編譯的模組中已變更，編譯器就會產生 C1307。  
  
 若要修正這項錯誤，請執行 \/LTCG:PGINSTRUMENT，重做所有測試回合，並執行 \/LTCG:PGOPTIMIZE。  如果不能執行 \/LTCG:PGINSTRUMENT 並重做所有測試回合，請使用 \/LTCG:PGUPDATE 代替 \/LTCG:PGOPTIMIZE，以建立最佳化影像。