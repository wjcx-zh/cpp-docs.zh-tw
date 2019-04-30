---
title: _CrtSetBreakAlloc
ms.date: 11/04/2016
apiname:
- _CrtSetBreakAlloc
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
- CrtSetBreakAlloc
- _CrtSetBreakAlloc
helpviewer_keywords:
- CrtSetBreakAlloc function
- _CrtSetBreakAlloc function
ms.assetid: 33bfc6af-a9ea-405b-a29f-1c2d4d9880a1
ms.openlocfilehash: bbc4b0de553533dde95f37675b3c9234569e3505
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64342959"
---
# <a name="crtsetbreakalloc"></a>_CrtSetBreakAlloc

在指定的物件配置順序編號設定中斷點 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
long _CrtSetBreakAlloc(
   long lBreakAlloc
);
```

### <a name="parameters"></a>參數

*lBreakAlloc*<br/>
要設定中斷點的配置順序編號。

## <a name="return-value"></a>傳回值

傳回有設定中斷點的上一個物件配置順序編號。

## <a name="remarks"></a>備註

**_CrtSetBreakAlloc**允許應用程式的記憶體配置的特定點中斷並追溯回要求的來源，以執行記憶體遺漏偵測。 此函式會在記憶體區塊配置於堆積中時，使用指派給記憶體區塊的循序物件配置順序編號。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtSetBreakAlloc**會在前置處理期間移除。

物件配置順序編號會儲存在定義於 Crtdbg.h 中的 **_CrtMemBlockHeader** 結構的 *lRequest* 欄位內。 當記憶體區塊的相關資訊由其中一個偵錯傾印函式報告時，此編號會包含在大括號，例如{36}。

如需有關如何 **_CrtSetBreakAlloc**可以搭配其他記憶體管理函式，請參閱[追蹤堆積配置要求](/visualstudio/debugger/crt-debug-heap-details)。 如需在偵錯版之基底堆積中如何配置、初始化及管理記憶體區塊的詳細資訊，請參閱 [CRT Debug Heap Details](/visualstudio/debugger/crt-debug-heap-details)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetBreakAlloc**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_setbrkal.c
// compile with: -D_DEBUG /MTd -Od -Zi -W3 /c /link -verbose:lib -debug

/*
* In this program, a call is made to the _CrtSetBreakAlloc routine
* to verify that the debugger halts program execution when it reaches
* a specified allocation number.
*/

#include <malloc.h>
#include <crtdbg.h>

int main( )
{
        long allocReqNum;
        char *my_pointer;

        /*
         * Allocate "my_pointer" for the first
         * time and ensure that it gets allocated correctly
         */
        my_pointer = malloc(10);
        _CrtIsMemoryBlock(my_pointer, 10, &allocReqNum, NULL, NULL);

        /*
         * Set a breakpoint on the allocation request
         * number for "my_pointer"
         */
        _CrtSetBreakAlloc(allocReqNum+2);

        /*
         * Alternate freeing and reallocating "my_pointer"
         * to verify that the debugger halts program execution
         * when it reaches the allocation request
         */
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
        my_pointer = malloc(10);
        free(my_pointer);
}
```

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
