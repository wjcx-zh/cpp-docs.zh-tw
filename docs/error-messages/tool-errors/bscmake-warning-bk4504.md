---
title: "BSCMAKE 警告 BK4504 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK4504"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK4504"
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# BSCMAKE 警告 BK4504
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

檔案包含太多參考; 忽略來自這個來源的進一步參考  
  
 .cpp 檔包含 64,000 個以上的符號參考。  當 BSCMAKE 發生在檔案中的 64,000 個參考，但進一步忽略所有參考。  
  
 若要修正這個問題，您可以將檔案分割成兩個以上的檔案，每一個有少於 64,000 符號參考，或使用 `#pragma component(browser)` 前置處理器指示詞限制產生供特定參考的符號。  如需詳細資訊，請參閱[元件](../../preprocessor/component.md)。