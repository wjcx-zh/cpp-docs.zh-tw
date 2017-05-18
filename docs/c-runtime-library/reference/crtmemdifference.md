---
title: _CrtMemDifference | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtMemDifference
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
- _CrtMemDifference
- CrtMemDifference
dev_langs:
- C++
helpviewer_keywords:
- CrtMemDifference function
- _CrtMemDifference function
ms.assetid: 0f327278-b551-482f-958b-76941f796ba4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 9793a58ed76b4c3251936b9016f8308ad06a07fb
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="crtmemdifference"></a>_CrtMemDifference
比較兩個記憶體狀態並傳回其差異 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
int _CrtMemDifference(   
   _CrtMemState *stateDiff,  
   const _CrtMemState *oldState,  
   const _CrtMemState *newState   
);  
```  
  
#### <a name="parameters"></a>參數  
 `stateDiff`  
 用來儲存兩個記憶體狀態 (已傳回) 之間差異的 `_CrtMemState` 結構指標。  
  
 `oldState`  
 較舊記憶體狀態 (`_CrtMemState` 結構) 的指標。  
  
 `newState`  
 較新記憶體狀態 (`_CrtMemState` 結構) 的指標。  
  
## <a name="return-value"></a>傳回值  
 如果記憶體狀態明顯不同， `_CrtMemDifference` 會傳回 TRUE。 否則，此函式會傳回 FALSE。  
  
## <a name="remarks"></a>備註  
 `_CrtMemDifference` 函式會比較 `oldState` 和 `newState` 並將其差異儲存在 `stateDiff`中，以供應用程式稍後用來偵測記憶體流失和其他記憶體問題。 未定義 [_DEBUG](../../c-runtime-library/debug.md) 時，會在前置處理期間移除 `_CrtMemDifference` 的呼叫。  
  
 `newState` 和 `oldState` 必須是 `_CrtMemState` 結構的有效指標、已在 Crtdbg.h 中定義，並且已由 [_CrtMemCheckpoint](../../c-runtime-library/reference/crtmemcheckpoint.md) 在呼叫 `_CrtMemDifference`前填入。 `stateDiff` 必須是先前配置之 `_CrtMemState` 結構執行個體的指標。 如果 `stateDiff`、`newState` 或 `oldState` 為 `NULL`，則會叫用無效的參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) 會設定為 `EINVAL`，且此函式會傳回 FALSE。  
  
 `_CrtMemDifference` 會比較 `oldState` 與 `newState` 中區塊的 `_CrtMemState` 欄位值，並將結果儲存在 `stateDiff` 中。 當兩個記憶體狀態中的已配置區塊類型數目或配置給每種類型的區塊總數不同時，表示這兩個狀態有很大的差異。 曾經配置給這兩個狀態的最大數量之間的差異，以及配置給這兩個狀態的總數之間的差異也會儲存在 `stateDiff`中。  
  
 根據預設，內部 C 執行階段區塊 (`_CRT_BLOCK`) 不會包含在記憶體狀態作業中。 您可以使用 [_CrtSetDbgFlag](../../c-runtime-library/reference/crtsetdbgflag.md) 函式來開啟 `_CRTDBG_CHECK_CRT_DF` 的 `_crtDbgFlag` 位元，以將這些區塊包含在流失偵測和其他記憶體狀態作業中。 已釋放的記憶體區塊 (`_FREE_BLOCK`) 不會使 `_CrtMemDifference` 傳回 TRUE。  
  
 如需堆積狀態函式和 `_CrtMemState` 結構的詳細資訊，請參閱 [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details)前填入。 如需如何在偵錯版本的基底堆積中配置、初始化和管理記憶體區塊的資訊，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_CrtMemDifference`|\<crtdbg.h>|\<errno.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
 **程式庫：**僅限偵錯版本的 [CRT 程式庫功能](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)
