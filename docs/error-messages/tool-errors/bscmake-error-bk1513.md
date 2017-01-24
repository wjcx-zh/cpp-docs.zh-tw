---
title: "BSCMAKE 錯誤 BK1513 | Microsoft Docs"
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
  - "BK1513"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK1513"
ms.assetid: 9ba87c09-8d82-4c80-b0cf-a8de63dcf9da
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# BSCMAKE 錯誤 BK1513
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

非累加式更新需要所有 .SBR 檔案  
  
 BSCMAKE 無法建置新的瀏覽資訊 \(.bsc\) 檔，因為一個或多個 .sbr 檔遭到截斷。  若要尋找遭截斷的 .sbr 檔案名稱，請參閱此錯誤隨附的 [BK4502](../../error-messages/tool-errors/bscmake-warning-bk4502.md) 警告。  
  
 BSCMAKE 可以將 .bsc 檔更新為遭截斷的 .sbr 檔，但無法建置新的 .bsc 檔。  BSCMAKE 可能會因為下列原因而建置新的 .bsc 檔：  
  
-   .bsc 檔遺失。  
  
-   指定給 .bsc 檔的檔案名稱錯誤。  
  
-   .bsc 檔損毀。  
  
 若要解決這個問題，請刪除被截斷的 .sbr 檔並重新建置，或清除方案並重建。  \(在 IDE 中，選擇 \[建置\]、\[清除方案\]，然後選擇 \[建置\]、\[重建方案\]。\)