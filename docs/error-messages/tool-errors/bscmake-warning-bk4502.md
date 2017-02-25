---
title: "BSCMAKE 警告 BK4502 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK4502"
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
  - "BK4502"
ms.assetid: ee412ec8-df03-4cdb-91ee-5d609ded8691
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# BSCMAKE 警告 BK4502
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

截斷的 .SBR 檔 'filename' 不在 filename 中  
  
 更新時指定了一個檔案長度為零的 .sbr 檔案，而該檔案並非原來所指定之 .bsc 檔案的一部分。  
  
### 若要修正，請檢查下列可能原因  
  
1.  指定的檔案名稱錯誤。  
  
2.  檔案已刪除 \(因錯誤 [BK1513](../../error-messages/tool-errors/bscmake-error-bk1513.md) 結果\)。  
  
3.  檔案損毀，必須使用 BSCMAKE 進行完整建置。