---
title: "專案建置錯誤 PRJ0031 | Microsoft Docs"
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
  - "PRJ0031"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0031"
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 專案建置錯誤 PRJ0031
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案 'file' 自訂建置步驟的 'Outputs' 屬性所含的 'macro' 計算結果為 'macro\_expansion'。  
  
 檔案的自訂建置步驟可能由於巨集評估問題而造成不良輸出。  此錯誤也可能表示檔案路徑的格式錯誤，其檔案路徑中包含不正確的字元或字元組合。  
  
 若要解決此問題，請修正巨集或修正路徑規格。  評估的路徑是專案目錄的絕對路徑。