---
title: _CrtSetAllocHook | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtSetAllocHook
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
- _CrtSetAllocHook
- CrtSetAllocHook
dev_langs:
- C++
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
caps.latest.revision: 15
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: fa03fb135907d9f516544f5f4b202c9f4e779fc3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/30/2017

---
# <a name="crtsetallochook"></a>_CrtSetAllocHook
將用戶端定義的配置函式連結到 C 執行階段偵錯記憶體配置處理序，以進行安裝 (僅限偵錯版本)。  
  
## <a name="syntax"></a>語法  
  
```  
_CRT_ALLOC_HOOK _CrtSetAllocHook(  
   _CRT_ALLOC_HOOK allocHook   
);  
```  
  
#### <a name="parameters"></a>參數  
 `allocHook`  
 要連結到 C 執行階段偵錯記憶體配置處理序之新的用戶端定義配置函式。  
  
## <a name="return-value"></a>傳回值  
 傳回先前定義的配置攔截函式；如果 `allocHook` 為 `NULL`，則為 `NULL`。  
  
## <a name="remarks"></a>備註  
 `_CrtSetAllocHook` 可讓應用程式將自己的配置函式連結到 C 執行階段偵錯程式庫記憶體配置處理序。 因此，每次呼叫偵錯配置函式以配置、重新配置或釋放記憶體區塊，都會觸發對應用程式攔截函式的呼叫。 `_CrtSetAllocHook` 提供應用程式一個簡單的方法，以測試應用程式如何處理記憶體不足的情況、檢查配置模式的能力，以及記錄配置資訊以供稍後分析的機會。 若未定義 [_DEBUG](../../c-runtime-library/debug.md)，將會在前置處理期間移除對 `_CrtSetAllocHook` 的呼叫。  
  
 `_CrtSetAllocHook` 函式會安裝 `allocHook` 中指定的新用戶端定義配置函式，並傳回先前定義的攔截函式。 下列範例示範用戶端定義的配置攔截程序應如何設計原型：  
  
```  
int YourAllocHook( int allocType, void *userData, size_t size, int   
blockType, long requestNumber, const unsigned char *filename, int   
lineNumber);  
```  
  
 `allocType` 引數指定觸發配置攔截函式呼叫的配置作業類型 `(_HOOK_ALLOC`、`_HOOK_REALLOC` 和 `_HOOK_FREE`)。 當觸發的配置類型是 `_HOOK_FREE` 時，`userData` 是即將要釋放之記憶體區塊的使用者資料區段指標。 不過，當觸發的配置類型是 `_HOOK_ALLOC` 或 `_HOOK_REALLOC` 時，由於尚未配置記憶體區塊，因此 `userData` 為 `NULL`。  
  
 `size` 指定記憶體區塊的大小 (以位元組為單位)，`blockType` 表示記憶體區塊的類型，`requestNumber` 是記憶體區塊的物件配置順序編號，而 `filename` 和 `lineNumber` (如果有) 指定起始觸發之配置作業的原始程式檔名和行號。  
  
 攔截函式完成處理之後，必須傳回布林值，以指示主要 C 執行階段配置處理序如何繼續執行。 如果攔截函式想要讓主要配置處理序以從未呼叫攔截函式的方式繼續執行，則攔截函式應傳回 `TRUE`。 這會導致執行原始觸發的配置作業。 攔截函式可以利用這項實作來收集和儲存配置資訊以供稍後分析，而不會干擾目前的配置作業或偵錯堆積的狀態。  
  
 如果攔截函式想要讓主要配置處理序以呼叫觸發之配置作業但失敗的方式繼續執行，則攔截函式應傳回 `FALSE`。 攔截函式可以利用這項實作來模擬各種不同的記憶體情況，並偵錯堆積狀態以測試應用程式如何處理每種情況。  
  
 若要清除攔截函式，請將 `NULL` 傳遞至 `_CrtSetAllocHook`。  
  
 如需如何搭配其他記憶體管理函式使用 `_CrtSetAllocHook`，以及如何撰寫您自己的用戶端定義攔截函式的詳細資訊，請參閱[撰寫偵錯攔截函式](/visualstudio/debugger/debug-hook-function-writing)。  
  
> [!NOTE]
> `/clr:pure` 下不支援  `_CrtSetAllocHook`。 **/clr:pure** 和 **/clr:safe** 編譯器選項在 Visual Studio 2015 中已被取代。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|  
|-------------|---------------------|  
|`_CrtSetAllocHook`|\<crtdbg.h>|  
  
 如需相容性的詳細資訊，請參閱＜簡介＞中的[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example"></a>範例  
 如需如何使用 `_CrtSetAllocHook` 的範例，請參閱 [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167)。  
  
## <a name="see-also"></a>另請參閱  
 [偵錯常式](../../c-runtime-library/debug-routines.md)   
 [_CrtGetAllocHook](../../c-runtime-library/reference/crtgetallochook.md)
