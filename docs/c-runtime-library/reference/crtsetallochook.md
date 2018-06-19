---
title: _CrtSetAllocHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8d86072ceb41b966adfca298152b6209450aace3
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32402061"
---
# <a name="crtsetallochook"></a>_CrtSetAllocHook

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

傳回預先定義的配置攔截函式或**NULL**如果*allocHook*是**NULL**。

## <a name="remarks"></a>備註

**_CrtSetAllocHook**允許應用程式連結到 C 執行階段偵錯程式庫的記憶體配置處理自己的配置函式。 因此，每次呼叫偵錯配置函式以配置、重新配置或釋放記憶體區塊，都會觸發對應用程式攔截函式的呼叫。 **_CrtSetAllocHook**應用程式提供簡單的方法來測試應用程式如何處理記憶體不足的情況下，檢查配置模式，並有機會稍後記錄供配置資訊的能力分析。 當[_DEBUG](../../c-runtime-library/debug.md)未定義時，呼叫 **_CrtSetAllocHook**會在前置處理期間移除。

**_CrtSetAllocHook**函式會安裝新的用戶端定義的配置函式中指定*allocHook*並傳回先前定義的攔截函式。 下列範例示範用戶端定義的配置攔截程序應如何設計原型：

```C
int YourAllocHook( int allocType, void *userData, size_t size,
                   int blockType, long requestNumber,
                   const unsigned char *filename, int lineNumber);
```

**AllocType**引數指定的配置作業類型 (**_HOOK_ALLOC**， **_HOOK_REALLOC**，和 **_HOOK_FREE**)，觸發配置攔截函式的呼叫。 當觸發配置類型是 **_HOOK_FREE**， *userData*即將要釋放的記憶體區塊的使用者資料區段的指標。 不過，當觸發配置類型是 **_HOOK_ALLOC**或 **_HOOK_REALLOC**， *userData*是**NULL**因為記憶體區塊尚未配置尚未。

*大小*指定大小的記憶體區塊以位元組為單位， *blockType*指出記憶體區塊類型*requestNumber*是物件配置順序編號的記憶體區塊，而且如果可用， *filename*和**lineNumber**指定原始程式檔名和行號何處起始觸發配置作業。

攔截函式完成處理之後，必須傳回布林值，以指示主要 C 執行階段配置處理序如何繼續執行。 攔截函式時想繼續如果如同永遠不會呼叫攔截函式，則應傳回攔截函式的主要配置程序**TRUE**。 這會導致執行原始觸發的配置作業。 攔截函式可以利用這項實作來收集和儲存配置資訊以供稍後分析，而不會干擾目前的配置作業或偵錯堆積的狀態。

攔截函式時想繼續如果呼叫觸發的配置作業，而且它失敗，則應傳回攔截函式的主要配置程序**FALSE**。 攔截函式可以利用這項實作來模擬各種不同的記憶體情況，並偵錯堆積狀態以測試應用程式如何處理每種情況。

若要清除的攔截函式，傳遞**NULL**至 **_CrtSetAllocHook**。

如需有關如何 **_CrtSetAllocHook**可以搭配其他記憶體管理函式或撰寫您自己的用戶端定義之 hook 函式，請參閱[偵錯攔截函式撰寫](/visualstudio/debugger/debug-hook-function-writing)。

> [!NOTE]
> **_CrtSetAllocHook**下，不支援 **/clr: pure**。 **/Clr: pure**和 **/clr: safe**編譯器選項會取代 Visual Studio 2015 中，在 Visual Studio 2017 中移除。

## <a name="requirements"></a>需求

|常式|必要的標頭|
|-------------|---------------------|
|**_CrtSetAllocHook**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

如需使用方式的範例 **_CrtSetAllocHook**，請參閱[crt_dbg2](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/crt/crt_dbg2)。

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetAllocHook](crtgetallochook.md)<br/>
