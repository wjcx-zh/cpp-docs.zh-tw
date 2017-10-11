---
title: __CxxFrameHandler | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __CxxFrameHandler
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr80.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr90.dll
- msvcr120.dll
apitype: DLLExport
f1_keywords:
- __CxxFrameHandler
dev_langs:
- C++
helpviewer_keywords:
- __CxxFrameHandler
ms.assetid: b79ac97f-425a-42ae-9b91-8beaef935333
caps.latest.revision: 3
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 75f900560f226557bc160bdf74df4467b0c7aa32
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="cxxframehandler"></a>__CxxFrameHandler
內部 CRT 函式。 供 CRT 用於處理結構化例外狀況框架。  
  
## <a name="syntax"></a>語法  
  
```cpp  
EXCEPTION_DISPOSITION __CxxFrameHandler(  
      EHExceptionRecord  *pExcept,  
      EHRegistrationNode *pRN,  
      void               *pContext,   
      DispatcherContext  *pDC  
   )  
```  
  
#### <a name="parameters"></a>參數  
 `pExcept`  
 傳遞至可能的 `catch` 陳述式的例外狀況記錄。  
  
 `pRN`  
 關於用於處理例外狀況的堆疊框架的動態資訊。 如需詳細資訊，請參閱 ehdata.h。  
  
 `pContext`  
 內容 (不用於 Intel 處理器)。  
  
 `pDC`  
 函式進入及堆疊框架的其他資訊。  
  
## <a name="return-value"></a>傳回值  
 [try-except 陳述式](../cpp/try-except-statement.md)所使用的其中一個「篩選條件運算式」值。  
  
## <a name="remarks"></a>備註  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|__CxxFrameHandler|excpt.h、ehdata.h|
