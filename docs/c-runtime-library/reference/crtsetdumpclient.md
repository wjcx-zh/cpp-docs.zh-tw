---
title: _CrtSetDumpClient | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetDumpClient
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
- _CrtSetDumpClient
- CrtSetDumpClient
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetDumpClient function
- CrtSetDumpClient function
ms.assetid: f3dd06d0-c331-4a12-b68d-25378d112033
caps.latest.revision: 12
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 035851454e2f163ea013a7240d6699db402565d3
ms.lasthandoff: 02/24/2017

---
# <a name="crtsetdumpclient"></a>_CrtSetDumpClient
安裝應用程式定義的函式以傾印 `_CLIENT_BLOCK` 類型記憶體區塊 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      _CRT_DUMP_CLIENT _CrtSetDumpClient(   
   _CRT_DUMP_CLIENT dumpClient   
);  
```  
  
#### <a name="parameters"></a>參數  
 `dumpClient`  
 要連結到 C 執行階段偵錯記憶體傾印處理序之新的用戶端定義記憶體傾印函式。  
  
## <a name="return-value"></a>傳回值  
 傳回先前定義的用戶端區塊傾印函式。  
  
## <a name="remarks"></a>備註  
 `_CrtSetDumpClient` 函式可讓應用程式將自己的函式連結到 C 執行階段偵錯記憶體傾印處理序，以傾印儲存在 `_CLIENT_BLOCK` 記憶體區塊中的物件。 因此，每當偵錯傾印函式 (例如 [_CrtMemDumpAllObjectsSince](../../c-runtime-library/reference/crtmemdumpallobjectssince.md) 或 [_CrtDumpMemoryLeaks](../../c-runtime-library/reference/crtdumpmemoryleaks.md)) 傾印 `_CLIENT_BLOCK` 記憶體區塊時，也會呼叫應用程式的傾印函式。 `_CrtSetDumpClient` 提供應用程式一個簡單的方法，來偵測記憶體流失，以及驗證或報告儲存在 `_CLIENT_BLOCK` 區塊中的資料內容。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetDumpClient` 的呼叫。  
  
 `_CrtSetDumpClient` 函式會安裝 `dumpClient` 中指定的新應用程式定義傾印函式，並傳回先前定義的傾印函式。 用戶端區塊傾印函式的範例如下所示：  
  
```  
void DumpClientFunction( void *userPortion, size_t blockSize );  
```  
  
 `userPortion` 引數是記憶體區塊之使用者資料部分開頭的指標，而 `blockSize` 指定配置的記憶體區塊大小 (以位元組為單位)。 用戶端區塊傾印函式必須傳回 `void`。 傳入 `_CrtSetDumpClient` 的用戶端傾印函式指標是定義在 Crtdbg.h 中的 `_CRT_DUMP_CLIENT` 類型：  
  
```  
typedef void (__cdecl *_CRT_DUMP_CLIENT)( void *, size_t );  
```  
  
 如需在 `_CLIENT_BLOCK` 類型記憶體區塊上操作之函式的詳細資訊，請參閱[用戶端區塊攔截函式](/visualstudio/debugger/client-block-hook-functions)。 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md) 函式可用來傳回區塊類型和子類型的相關資訊。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_CrtSetDumpClient`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtReportBlockType](../../c-runtime-library/reference/crtreportblocktype.md)   
 [_CrtGetDumpClient](../../c-runtime-library/reference/crtgetdumpclient.md)
