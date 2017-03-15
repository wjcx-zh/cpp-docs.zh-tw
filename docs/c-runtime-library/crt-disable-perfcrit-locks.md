---
title: "_CRT_DISABLE_PERFCRIT_LOCKS | Microsoft Docs"
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
  - "_CRT_DISABLE_PERFCRIT_LOCKS"
  - "CRT_DISABLE_PERFCRIT_LOCKS"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_CRT_DISABLE_PERFCRIT_LOCKS 常數"
  - "CRT_DISABLE_PERFCRIT_LOCKS 常數"
ms.assetid: 36cc2d86-cdb1-4b2b-a03c-c0d3818e7c6f
caps.latest.revision: 4
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _CRT_DISABLE_PERFCRIT_LOCKS
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使 I\/O 作業的效能關鍵鎖定失效。  
  
## 語法  
  
```  
#define _CRT_DISABLE_PERFCRIT_LOCKS  
```  
  
## 備註  
 定義這個符號可以強制任何 I\/O 作業假設單一執行緒的 I\/O 模型改善在單一執行緒的 I\/O 繫結程式的效能。  如需詳細資訊，請參閱[多執行緒程式庫效能](../c-runtime-library/multithreaded-libraries-performance.md)。  
  
## 請參閱  
 [全域常數](../c-runtime-library/global-constants.md)