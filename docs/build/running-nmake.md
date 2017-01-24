---
title: "執行 NMAKE | Microsoft Docs"
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
  - "命令檔"
  - "命令檔, NMAKE"
  - "NMAKE 程式, 執行"
  - "NMAKE 程式, 目標"
  - "回應檔, NMAKE"
  - "目標"
  - "目標, 建置"
ms.assetid: 0421104d-8b7b-4bf3-86c1-928d9b7c1a8c
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 執行 NMAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
NMAKE [option...] [macros...] [targets...] [@commandfile...]  
```  
  
## 備註  
 NMAKE 只建置指定的目標，或如果沒有指定任何目標，就會建置 Makefile 中的第一個目標。  第一個 Makefile 目標是可以建置其他目標的[虛擬目標](../build/pseudotargets.md) \(Pseudotarget\)。  NMAKE 使用以 \/F 指定的 Makefile，如果沒有指定 \/F，便會使用在目前目錄中的 Makefile 檔案。  如果沒有指定 Makefile，則會使用推斷規則建置命令列目標。  
  
 `commandfile` 文字檔 \(或回應檔\) 含有命令列輸入。  其他輸入可以在 @`commandfile` 之前或之後。  允許使用路徑。  在 `commandfile` 中，將分行符號視為空格。  如果巨集定義包含空格，請以引號括住這些定義。  
  
## 您還想知道關於哪些方面的詳細資訊？  
 [NMAKE 選項](../build/nmake-options.md)  
  
 [Tools.ini 和 NMAKE](../build/tools-ini-and-nmake.md)  
  
 [NMAKE 的結束代碼](../build/exit-codes-from-nmake.md)  
  
## 請參閱  
 [NMAKE 參考](../build/nmake-reference.md)