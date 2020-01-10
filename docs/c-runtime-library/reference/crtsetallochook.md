---
title: _CrtSetAllocHook
ms.date: 11/04/2016
api_name:
- _CrtSetAllocHook
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _CrtSetAllocHook
- CrtSetAllocHook
helpviewer_keywords:
- _CrtSetAllocHook function
- CrtSetAllocHook function
ms.assetid: 405df37b-2fd1-42c8-83bc-90887f17f29d
ms.openlocfilehash: 303f682b54abc5e44cb7fdd4c89012dd9913288b
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938489"
---
# <a name="_crtsetallochook"></a>_CrtSetAllocHook

將用戶端定義的配置函式連結到 C 執行階段偵錯記憶體配置處理序，以進行安裝 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
_CRT_ALLOC_HOOK _CrtSetAllocHook(
   _CRT_ALLOC_HOOK allocHook
);
```

### <a name="parameters"></a>參數

*allocHook*<br/>
要連結到 C 執行階段偵錯記憶體配置處理序之新的用戶端定義配置函式。

## <a name="return-value"></a>傳回值

傳回先前定義的配置攔截函式，如果*allocHook*為**null**，則傳回**null** 。

## <a name="remarks"></a>備註

**_CrtSetAllocHook**可讓應用程式將自己的配置函式連結到 C 執行時間的 debug 程式庫記憶體配置進程。 因此，每次呼叫偵錯配置函式以配置、重新配置或釋放記憶體區塊，都會觸發對應用程式攔截函式的呼叫。 **_CrtSetAllocHook**提供一個簡單的方法，讓您測試應用程式如何處理記憶體不足的情況、檢查配置模式的能力，以及記錄配置資訊以供稍後分析的機會。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtSetAllocHook**的呼叫。

**_CrtSetAllocHook**函數會安裝*allocHook*中指定的新用戶端定義配置函式，並傳回先前定義的攔截函數。 下列範例示範用戶端定義的配置攔截程序應如何設計原型：

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType**引數會指定觸發呼叫配置攔截函式的配置作業類型（ **_HOOK_ALLOC**、 **_HOOK_REALLOC**和 **_HOOK_FREE**）。 當觸發的配置類型是 **_HOOK_FREE**時， *userData*是記憶體區塊的使用者資料區段的指標，即將釋放出來。 不過，當觸發的配置類型是 **_HOOK_ALLOC**或 **_HOOK_REALLOC**時， *userData*是**Null** ，因為尚未配置記憶體區塊。

*size*指定記憶體區塊的大小（以位元組為單位）， *blockType*表示記憶體區塊的類型， *requestNumber*是記憶體區塊的物件配置順序編號，如果可用的話， *filename*和**lineNumber**指定起始觸發配置作業的來原始檔案名和行號。

攔截函式完成處理之後，必須傳回布林值，以指示主要 C 執行階段配置處理序如何繼續執行。 當攔截函式想要讓主要配置進程繼續執行，如同從未呼叫過攔截函式一樣，攔截函式應該會傳回**TRUE**。 這會導致執行原始觸發的配置作業。 攔截函式可以利用這項實作來收集和儲存配置資訊以供稍後分析，而不會干擾目前的配置作業或偵錯堆積的狀態。

當攔截函式想要讓主要配置進程繼續執行，如同呼叫觸發配置作業且失敗時，攔截函式應該會傳回**FALSE**。 攔截函式可以利用這項實作來模擬各種不同的記憶體情況，並偵錯堆積狀態以測試應用程式如何處理每種情況。

若要清除攔截函式，請將**Null**傳遞給 **_CrtSetAllocHook**。

如需如何搭配其他記憶體管理函式使用 **_CrtSetAllocHook** ，或如何撰寫您自己的用戶端定義攔截函數的詳細資訊，請參閱[Debug 攔截函數寫入](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> **/Clr： pure**下不支援 **_CrtSetAllocHook** 。 **/Clr： pure**和 **/clr： safe**編譯器選項在 Visual Studio 2015 中已被取代，並已在 Visual Studio 2017 中移除。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需如何使用 **_CrtSetAllocHook**的範例，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
