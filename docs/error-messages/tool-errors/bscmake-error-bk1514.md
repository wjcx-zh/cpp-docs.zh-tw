---
title: "BSCMAKE 錯誤 BK1514 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1514"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1514"
ms.assetid: 7c7e2504-a490-44ab-bb1f-47385ee2f4b0
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# BSCMAKE 錯誤 BK1514
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

所有 .SBR 檔被截斷，在 filename 中找不到  
  
 沒有任何指定要更新的 .sbr 檔案是原來的瀏覽資訊檔案 \(.bsc\) 的一部分。  若要找出造成這個錯誤的 .sbr 檔案名稱，請讀取在此錯誤之前出現的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。  
  
### 若要修正，請檢查下列可能原因  
  
1.  指定的 .sbr 或 .bsc 檔案名稱錯誤。  
  
2.  損毀的 .bsc 檔案必須使用 BSCMAKE 重建。