---
title: "專案建置錯誤 PRJ0006 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0006"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0006"
ms.assetid: ce092be4-1652-414f-8cb5-b97ef5841f89
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 專案建置錯誤 PRJ0006
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

無法開啟暫存檔案 'file'，請確認該檔案存在，且該目錄並非寫入保護。  
  
 Visual C\+\+ 在建置過程無法建立暫存檔案。  這個問題的原因包括：  
  
-   沒有暫存目錄。  
  
-   暫存目錄為唯讀。  
  
-   磁碟空間不足。  
  
-   \[$\(IntDir\)\] 資料夾為唯讀資料夾，或包含唯讀的暫存檔案。  
  
 這個錯誤也會發生下列錯誤 PRJ0007：無法建立輸出目錄 'directory'。  錯誤 PRJ0007 表示無法建立 $\(IntDir\) 目錄，意即建立暫存檔案也會失敗。  
  
 每當您指定下列各項時，都會建立暫存檔案：  
  
-   回應檔 \(Response File\)。  
  
-   自訂建置步驟。  
  
-   建置事件。