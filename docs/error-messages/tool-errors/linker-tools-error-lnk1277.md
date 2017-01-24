---
title: "連結器工具錯誤 LNK1277 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1277"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1277"
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 連結器工具錯誤 LNK1277
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

在 pgd \(檔名\) 中找不到物件記錄  
  
 使用 [\/LTCG:PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md) 時，輸入 .lib、def 或 .obj 檔的其中一個路徑與在 \/LTCG:PGINSTRUMENT 期間所找到的路徑不同。  這可能是因為 LIB 環境變數在 \/LTCG:PGINSTRUMENT 之後變更所造成。  輸入檔案的完整路徑是儲存在 .pgd 檔中。  
  
 \/LTCG:PGOPTIMIZE 會要求輸入必須與 \/LTCG:PGINSTRUMENT 階段完全相同。  
  
 若要解除這項警告，請執行下列任一種方法：  
  
-   執行 \/LTCG:PGINSTRUMENT，重做所有測試回合，並執行 \/LTCG:PGOPTIMIZE。  
  
-   將 LIB 環境變數變更為當您執行 \/LTCG:PGINSTRUMENT 時的狀況。  
  
 不建議您使用 \/LTCG:PGUPDATE 來解決 LNK1277。