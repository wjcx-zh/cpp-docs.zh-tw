---
title: _CrtMemDumpAllObjectsSince | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDumpAllObjectsSince
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
- CrtMemDumpAllObjectsSince
- _CrtMemDumpAllObjectsSince
dev_langs:
- C++
helpviewer_keywords:
- _CrtMemDumpAllObjectsSince function
- CrtMemDumpAllObjectsSince function
ms.assetid: c48a447a-e6bb-475c-9271-a3021182a0dc
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c1c04d21b1c4009bd93e608d1c243d5b459e2422
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/29/2018
---
# <a name="crtmemdumpallobjectssince"></a>_CrtMemDumpAllObjectsSince
從程式執行一開始，或從指定的堆積狀態傾印堆積中物件的相關資訊 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      void _CrtMemDumpAllObjectsSince(   
   const _CrtMemState *state   
);  
```  
  
#### <a name="parameters"></a>參數  
 `state`  
 要開始傾印之來源堆積狀態的指標，或為 **NULL**。  
  
## <a name="remarks"></a>備註  
 `_CrtMemDumpAllObjectsSince` 函式會以使用者可讀格式傾印堆積中所配置之物件的偵錯標頭資訊。 應用程式會使用此傾印資訊追蹤配置及偵測記憶體問題。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtMemDumpAllObjectsSince` 的呼叫。  
  
 `_CrtMemDumpAllObjectsSince` 使用 `state` 參數的值來判斷起始傾印作業的位置。 若要從指定的堆積狀態開始傾印，`state` 參數必須是已由 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 在呼叫 `_CrtMemDumpAllObjectsSince` 前填入之 **_CrtMemState** 結構的指標。 當 `state` 為 **NULL** 時，函式會從程式執行一開始就開始傾印。  
  
 如果應用程式已藉由呼叫 [_CrtSetDumpClient](../../c-runtime-library/reference/crtsetdumpclient.md) 安裝傾印攔截函式，則每次 `_CrtMemDumpAllObjectsSince` 傾印 `_CLIENT_BLOCK` 類型區塊的相關資訊時，也會呼叫應用程式提供的傾印函式。 根據預設，內部 C 執行階段區塊 (`_CRT_BLOCK`) 不會包含在記憶體傾印作業中。 您可以使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式來開啟 **_crtDbgFlag** 的 `_CRTDBG_CHECK_CRT_DF` 位元，以包含這些區塊。 此外，標記為釋出或略過 (**_FREE_BLOCK**、**_IGNORE_BLOCK**) 的區塊不會包含在記憶體傾印中。  
  
 如需堆積狀態函式和 `_CrtMemState` 結構的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式傳回的值|必要的標頭|  
|-------------|---------------------|  
|**_CrtMemDumpAll-ObjectsSince**|\<crtdbg.h>|  
  
 如需相容性詳細資訊，請參閱簡介中的 [相容性](../../c-runtime-library/compatibility.md) 。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `_CrtMemDumpAllObjectsSince` 的範例，請參閱 [crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。  
  
## <a name="see-also"></a>請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)