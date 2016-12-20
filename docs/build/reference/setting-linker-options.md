---
title: "設定連結器選項 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "檔案 [C++], LINK"
  - "輸入檔 [C++]"
  - "輸入檔 [C++], 連結器"
  - "連結器 [C++], 參數"
  - "連結器 [C++], 設定選項的方法"
  - "物件/程式庫模組"
ms.assetid: e08fb487-0f2e-4f24-87db-232dbc8bd2e2
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 設定連結器選項
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

連結器選項在開發環境內、外都可以設定。  每一項連結器選項的主題都會討論如何在開發環境中設定。  如需完整的清單，請參閱[連結器選項](../../build/reference/linker-options.md)。  
  
 當您在開發環境之外執行 LINK 時，您可以用下列一種或數種方式指定輸入：  
  
-   在[命令列](../../build/reference/linker-command-line-syntax.md)上  
  
-   使用[命令檔](../../build/reference/link-command-files.md)  
  
-   在[環境變數](../../build/reference/link-environment-variables.md)中  
  
 LINK 首先會處理 LINK 環境變數中指定的選項，接下來依照命令列及命令檔中所指定選項的順序處理。  如果某一選項重複出現而且具有不同引數，則以最後處理的一個為準。  
  
 各種選項均套用至整個組建；任何選項都不能只套用至特定的輸入檔案。  
  
## 請參閱  
 [C\/C\+\+ 建置參考](../../build/reference/c-cpp-building-reference.md)   
 [連結器選項](../../build/reference/linker-options.md)