---
title: "專案建置錯誤 PRJ0034 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "PRJ0034"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "PRJ0034"
ms.assetid: 1da4a55b-231b-4476-8545-6997628fbc00
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# 專案建置錯誤 PRJ0034
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

專案層級自訂建置步驟的 'Additional Dependencies' 屬性所含的 'macro' 計算結果為 'macro\_expansion'。  
  
 檔案的自訂建置步驟可能由於巨集評估問題，而使它的額外相依性中包含錯誤。  此錯誤也可能表示檔案路徑的格式錯誤，其檔案路徑中包含不正確的字元或字元組合。  
  
 若要解決此問題，請修正巨集或修正路徑規格。  評估的路徑是專案目錄的絕對路徑。