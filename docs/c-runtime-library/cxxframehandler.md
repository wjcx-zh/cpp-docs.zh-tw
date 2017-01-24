---
title: "__CxxFrameHandler | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "__CxxFrameHandler"
apilocation: 
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr100.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr90.dll"
  - "msvcr120.dll"
apitype: "DLLExport"
f1_keywords: 
  - "__CxxFrameHandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__CxxFrameHandler"
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 3
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# __CxxFrameHandler
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

內部 CRT 函式。  供 CRT 用於處理結構化例外狀況框架。  
  
## 語法  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(       EHExceptionRecord  *pExcept,       EHRegistrationNode *pRN,       void               *pContext,        DispatcherContext  *pDC    )  
```  
  
#### 參數  
 `pExcept`  
 傳遞至可能的 `catch` 陳述式的例外狀況記錄。  
  
 `pRN`  
 關於用於處理例外狀況的堆疊框架的動態資訊。  如需詳細資訊，請參閱 ehdata.h。  
  
 `pContext`  
 內容  \(不用於 Intel 處理器\)。  
  
 `pDC`  
 函式進入及堆疊框架的其他資訊。  
  
## 傳回值  
 [try\-except 陳述式](../cpp/try-except-statement.md) 所使用的其中一個*「篩選條件運算式」*\(Filter Expression\) 值。  
  
## 備註  
  
## 需求  
  
|常式|必要的標頭|  
|--------|-----------|  
|\_\_CxxFrameHandler|excpt.h、ehdata.h|