---
title: "/Q 選項 (低階運算) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/q"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Q 編譯器選項 [C++]"
  - "-Q 編譯器選項 [C++]"
  - "/Q 編譯器選項 [C++]"
ms.assetid: 9fa738b9-630a-4bde-bc87-bdfa30552be4
caps.latest.revision: 24
caps.handback.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /Q 選項 (低階運算)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

您可以使用 **\/Q** 編譯器選項以執行下列低階編譯器運算：  
  
-   [\/Qfast\_transcendentals \(Force Fast Transcendentals\)](../../build/reference/qfast-transcendentals-force-fast-transcendentals.md)：產生快速超越函式。  
  
-   [\/QIfist \(抑制 \_ftol\)](../../build/reference/qifist-suppress-ftol.md)：在必須從浮點型別轉換為整數型別時，抑制 `_ftol` \(僅適用於 x86\)。  
  
-   [\/Qimprecise\_fwaits \(移除 Try 區域內的 fwaits\)](../../build/reference/qimprecise-fwaits-remove-fwaits-inside-try-blocks.md)：移除 `try` 區塊內的 `fwait` 命令。  
  
-   [\/Qpar \(自動平行化工具\)](../../build/reference/qpar-auto-parallelizer.md): 讓有標記 [\#pragma loop\(\)](../../preprocessor/loop.md) 的迴圈自動化平行運作。  
  
-   [\/Qpar\-report \(自動平行化工具報告層級\)](../../build/reference/qpar-report-auto-parallelizer-reporting-level.md): 啟用自動平行處理的報告層級。  
  
-   [\/Qsafe\_fp\_loads](../../build/reference/qsafe-fp-loads.md): 抑制最佳化浮點暫存器載入和在記憶體和 MMX 之間移動的暫存器。  
  
-   [\/Qvec\-report \(自動向量化工具報告層級\)](../../build/reference/qvec-report-auto-vectorizer-reporting-level.md): 啟用自動向量化的報告層級。  
  
## 請參閱  
 [編譯器選項](../../build/reference/compiler-options.md)   
 [設定編譯器選項](../../build/reference/setting-compiler-options.md)