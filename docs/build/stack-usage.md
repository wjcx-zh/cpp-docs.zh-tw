---
title: "堆疊使用方式 | Microsoft Docs"
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
ms.assetid: 383f0072-0438-489f-8829-cca89582408c
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# 堆疊使用方式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

超出 RSP 目前位址的所有記憶體，都會被視為變動 \(Volatile\) 記憶體：在使用者偵錯工作階段或中斷處理常式期間，OS \(或偵錯工具\) 可能會覆寫這個記憶體。  因此，在嘗試讀取或將值寫入堆疊框架之前，一定要先設定 RSP。  
  
 這個章節將討論區域變數和 **alloca** 內建 \(Intrinsic\) 的堆疊空間配置。  
  
-   [堆疊配置](../build/stack-allocation.md)  
  
-   [動態參數堆疊區域建構](../build/dynamic-parameter-stack-area-construction.md)  
  
-   [函式型別](../build/function-types.md)  
  
-   [malloc 對齊](../build/malloc-alignment.md)  
  
-   [alloca](../build/alloca.md)  
  
## 請參閱  
 [x64 軟體慣例](../build/x64-software-conventions.md)