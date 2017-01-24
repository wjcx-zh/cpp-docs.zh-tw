---
title: "專案建置錯誤 PRJ0009 | Microsoft Docs"
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
  - "PRJ0009"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0009"
ms.assetid: 89291778-cda4-495d-983f-ddcc06dfc98b
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0009
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟建置記錄來執行寫入。  
  
 **請確認其他處理序並未開啟該檔案，且並非寫入保護。**  
  
 Visual C\+\+ 在將 **Build Logging** 屬性設為 **Yes** 並執行建置或重建之後，無法在獨佔模式下開啟組建記錄。  
  
 檢查 \[建置記錄\] 設定，方法為開啟 \[**選項**\] 對話方塊 \(在 \[工具\] 功能表上按一下 \[**選項**\] 命令\)，然後選取 \[專案\] 資料夾中的 \[VC\+\+ 建置\]。  這個建置檔案稱為 BuildLog.htm，而且是寫入中繼目錄 $\(IntDir\) 中。  
  
 這個錯誤的可能原因是：  
  
-   您正在執行兩個 Visual C\+\+ 處理序，並試圖同時在兩者中建置相同專案的相同組態。  
  
-   在鎖定檔案的處理序中開啟組建記錄。  
  
-   使用者沒有建立檔案的權限。  
  
-   目前的使用者無 BuildLog.htm 檔案的寫入權限。