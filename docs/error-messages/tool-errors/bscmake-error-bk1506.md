---
title: "BSCMAKE 錯誤 BK1506 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK1506"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1506"
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# BSCMAKE 錯誤 BK1506
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟檔案 'filename' \[: reason\]  
  
 BSCMAKE 無法開啟檔案。  
  
### 若要修正，請檢查下列可能原因  
  
1.  檔案被其他處理序 \(Process\) 鎖定。  如果 `reason` 顯示「使用權限遭拒」，可能是瀏覽器正在使用此檔案。  請關閉瀏覽器視窗並嘗試重新建置。  
  
2.  磁碟已滿。  
  
3.  硬體錯誤。  
  
4.  指定的輸出檔案與現有的子目錄名稱相同。