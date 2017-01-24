---
title: "spawn 常數 | Microsoft Docs"
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
  - "_P_NOWAIT"
  - "_P_OVERLAY"
  - "_P_WAIT"
  - "_P_DETACH"
  - "_P_NOWAITO"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_P_DETACH 常數"
  - "_P_NOWAIT 常數"
  - "_P_NOWAITO 常數"
  - "_P_OVERLAY 常數"
  - "_P_WAIT 常數"
  - "P_DETACH 常數"
  - "P_NOWAIT 常數"
  - "P_NOWAITO 常數"
  - "P_OVERLAY 常數"
  - "P_WAIT 常數"
  - "spawn 常數"
ms.assetid: e0533e88-d362-46fc-b53c-5f193226d879
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# spawn 常數
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## 語法  
  
```  
#include <process.h>  
```  
  
## 備註  
 在繁衍作業期間前和期間中， `mode` 引數識別呼叫程序所採取的動作。  `mode` 的下列值的是可能出現的:  
  
|常數|意義|  
|--------|--------|  
|`_P_OVERLAY`|用新程序覆疊呼叫程序，破壞函式呼叫程序 \(與 `_exec` 呼叫作用相同\)。|  
|`_P_WAIT`|暫停呼叫執行緒，直到處理序的完成執行 \(同步 `_spawn`\)。|  
|`_P_NOWAIT`, `_P_NOWAITO`|繼續與新處理序 \(非同步 `_spawn`\) 同時執行呼叫程序。|  
|`_P_DETACH`|繼續執行呼叫程序;處理序在背景執行，沒有對主控台或鍵盤上的存取。  呼叫 `_cwait` 至新處理序將會失敗。  這是一項非同步 `_spawn`。|  
  
## 請參閱  
 [\_spawn、\_wspawn 函式](../c-runtime-library/spawn-wspawn-functions.md)   
 [全域常數](../c-runtime-library/global-constants.md)