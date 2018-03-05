---
title: __dllonexit | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- __dllonexit
apilocation:
- msvcrt.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr100.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- __dllonexit
dev_langs:
- C++
helpviewer_keywords:
- __dllonexit
ms.assetid: 708f2ceb-f95c-46b0-a58d-d68b3fa36f12
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7ed3b28381b92f4f11e4be99f97a2615a8379274
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="dllonexit"></a>__dllonexit
登錄要在結束時呼叫的常式。  
  
## <a name="syntax"></a>語法  
  
```  
_onexit_t __dllonexit(   _onexit_t func,  
   _PVFV **  pbegin,   
   _PVFV **  pend   
   )  
```  
  
#### <a name="parameters"></a>參數  
 `func`  
 要在結束時執行的函式指標。  
  
 `pbegin`  
 變數指標，指向要在中斷連結時執行的函式的清單開頭。  
  
 `pend`  
 變數指標，指向要在中斷連結時執行的函式的清單結尾。  
  
## <a name="return-value"></a>傳回值  
 如果成功，則為使用者的函式指標。 否則為 NULL 指標。  
  
## <a name="remarks"></a>備註  
 `__dllonexit` 函式類似 [_onexit](../c-runtime-library/reference/onexit-onexit-m.md) 函式，只不過這個常式看不到該函式所用的全域變數。 此函數使用 `pbegin` 和 `pend` 參數，而不是全域變數。  
  
 DLL 中與 MSVCRT.LIB 連結的 `_onexit` 和 `atexit` 函式，必須維護其本身的 atexit/_onexit 清單。 此常式是這類 DLL 呼叫的背景工作。  
  
 `_PVFV` 類型定義為 `typedef void (__cdecl *_PVFV)(void)`。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要檔案|  
|-------------|-------------------|  
|__dllonexit|onexit.c|  
  
## <a name="see-also"></a>請參閱  
 [_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)