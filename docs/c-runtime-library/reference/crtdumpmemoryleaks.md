---
title: _CrtDumpMemoryLeaks | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDumpMemoryLeaks
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords:
- CRTDBG_LEAK_CHECK_DF
- CRTDBG_CHECK_CRT_DF
- _CRTDBG_LEAK_CHECK_DF
- CrtDumpMemoryLeaks
- _CrtDumpMemoryLeaks
- _CRTDBG_CHECK_CRT_DF
dev_langs:
- C++
helpviewer_keywords:
- CrtDumpMemoryLeaks function
- CRTDBG_LEAK_CHECK_DF macro
- _CRTDBG_LEAK_CHECK_DF macro
- _CrtDumpMemoryLeaks function
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: 71b2eab4-7f55-44e8-a55a-bfea4f32d34c
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 799cb3a867af9695fcb72ae6d681168f604d880f
ms.contentlocale: zh-tw
ms.lasthandoff: 10/09/2017

---
# <a name="crtdumpmemoryleaks"></a>_CrtDumpMemoryLeaks
發生記憶體流失時，傾印偵錯堆積中的所有記憶體區塊 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
  
int _CrtDumpMemoryLeaks( void );  
```  
  
## <a name="return-value"></a>傳回值  
 如果發現記憶體流失，`_CrtDumpMemoryLeaks` 會傳回 TRUE。 否則，此函式會傳回 FALSE。  
  
## <a name="remarks"></a>備註  
 `_CrtDumpMemoryLeaks` 函式會判斷自程式執行開始以來是否發生記憶體流失。 發現流失時，會以使用者可讀格式傾印堆積中所有物件的偵錯標頭資訊。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtDumpMemoryLeaks` 的呼叫。  
  
 程式執行結束時經常會呼叫 `_CrtDumpMemoryLeaks`，以確認應用程式所配置的所有記憶體皆已釋放。 您可以使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式開啟 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md) 旗標的 `_CRTDBG_LEAK_CHECK_DF` 位元欄位，以在程式終止時自動呼叫此函式。  
  
 `_CrtDumpMemoryLeaks` 會呼叫[_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 以取得堆積的目前狀態，然後掃描尚未釋放之區塊的狀態。 遇到未釋放的區塊時，`_CrtDumpMemoryLeaks` 會呼叫 [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 以傾印自程式執行開始以來在堆積中配置之所有物件的資訊。  
  
 根據預設，內部 C 執行階段區塊 (`_CRT_BLOCK`) 不會包含在記憶體傾印作業中。 您可以使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式來開啟 `_crtDbgFlag` 的 `_CRTDBG_CHECK_CRT_DF` 位元，以將這些區塊包含在流失偵測處理序中。  
  
 如需堆積狀態函式和 `_CrtMemState` 結構的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需如何在偵錯版本的基底堆積中配置、初始化和管理記憶體區塊的詳細資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_CrtDumpMemoryLeaks`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `_CrtDumpMemoryLeaks` 的範例，請參閱 [crt_dbg1](http://msdn.microsoft.com/en-us/17b4b20c-e849-48f5-8eb5-dca6509cbaf9)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)
