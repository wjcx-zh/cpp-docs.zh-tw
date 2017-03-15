---
title: "連結器工具錯誤 LNK1140 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1140"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1140"
ms.assetid: 468d7651-a7cd-47b9-aead-5bb2fab56121
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# 連結器工具錯誤 LNK1140
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

程式資料庫的模組太多；以 \/PDB:NONE 連結  
  
 專案包含超過 4096 個模組。  
  
### 若要採用下列可能解決方式以進行修正  
  
1.  使用 [\/PDB:NONE](../../build/reference/pdb-use-program-database.md) 重新連結。  
  
2.  某些模組在不需偵錯資訊情形下進行編譯。  
  
3.  減少模組數目。