---
title: "連結器工具錯誤 LNK1200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1200"
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# 連結器工具錯誤 LNK1200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

讀取程式資料庫 'filename' 時發生錯誤  
  
 無法讀取程式資料庫 \(PDB\)。  
  
 錯誤的原因可能是檔案損毀。  
  
 如果 `filename` 是目的檔的 PDB，請使用 [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md) 重新編譯該目的檔。  
  
 如果 `filename` 是主要輸出檔的 PDB，且錯誤是發生在累加連結 \(Incremental Link\) 期間，請刪除 PDB 並重新連結。