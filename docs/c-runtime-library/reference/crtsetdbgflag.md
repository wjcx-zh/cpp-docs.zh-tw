---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: 8506b593a579c8dd1791e56c320bd9d8e2ee9ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938619"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

擷取或修改 **_crtDbgFlag** 旗標的狀態，以控制偵錯堆積管理員的配置行為 (僅限偵錯版本)。

## <a name="syntax"></a>語法

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>參數

*newFlag*<br/>
**_crtDbgFlag** 的新狀態。

## <a name="return-value"></a>傳回值

傳回 **_crtDbgFlag** 先前的狀態。

## <a name="remarks"></a>備註

**_CrtSetDbgFlag**函式可讓應用程式透過修改 **_crtDbgFlag**旗標的位欄位，來控制 debug 堆積管理員如何追蹤記憶體配置。 應用程式可透過設定位元 (開啟)，指示偵錯堆積管理員執行特定偵錯作業，包含在應用程式結束時檢查記憶體遺漏並在發現任何問題時進行回報，以及藉由指定已釋放的記憶體區塊應保留在堆積的連結清單中來模擬低記憶體的情況，還有在每次配置要求時透過檢查每個記憶體區塊來驗證堆積的完整性。 未定義[_debug](../../c-runtime-library/debug.md)時，會在前置處理期間移除對 **_CrtSetDbgFlag**的呼叫。

下表列出 **_crtDbgFlag** 的位元欄位，並描述它們的行為。 因為設定位元會導致增加診斷輸出，並降低程式執行速度，所以預設不會設定這些位元 (關閉)。 如需這些位元欄位的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。

|位元欄位|預設|說明|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|ON|的啟用 debug 堆積配置，並使用記憶體區塊類型識別碼，例如 **_CLIENT_BLOCK**。 停止將新的配置加入至堆積的連結清單，但將區塊類型設定為 **_IGNORE_BLOCK**。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|的在每個配置和解除配置要求時呼叫[_CrtCheckMemory](crtcheckmemory.md) 。 OFF：必須明確呼叫 **_CrtCheckMemory** 。<br /><br /> 堆積頻率檢查巨集會在設定此旗標時沒有效果。|
|**_CRTDBG_CHECK_CRT_DF**|OFF|的包含流失偵測和記憶體狀態差異作業中的 **_CRT_BLOCK**類型。 停止這些作業會忽略執行時間程式庫內部所使用的記憶體。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|的將釋放的記憶體區塊保留在堆積的連結清單中，將 **_FREE_BLOCK**類型指派給它們，並以 Byte 值0xDD 填入。 停止請勿將釋放的區塊保留在堆積的連結清單中。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|的在程式結束時，透過呼叫[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)執行自動流失檢查，並在應用程式無法釋放其配置的所有記憶體時產生錯誤報表。 停止請勿在程式結束時自動執行流失檢查。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|

**堆積檢查頻率巨集**

您可以根據**malloc**、 **realloc**、 **free**和 **_msize**的呼叫次數，指定 C 執行時間程式庫執行 debug 堆積（ **_CrtCheckMemory**）驗證的頻率。

然後， **_CrtSetDbgFlag**會檢查*newFlag*參數的前16個位是否有一個值。 指定的值是 **_CrtCheckMemory**呼叫之間的**malloc**、 **realloc**、 **free**和 **_msize**呼叫數目。 針對此用途有四個預先定義的巨集。

|巨集|_CrtCheckMemory 呼叫之間，呼叫 malloc、realloc、free 及 _msize 的次數|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (根據預設沒有檢查任何堆積)|

根據預設， **_CrtCheckMemory**會每隔1024次呼叫**malloc**、 **realloc**、 **free**和 **_msize**一次。

例如，您可以使用下列程式碼，指定堆積檢查每16個**malloc**、 **realloc**、 **free**和 **_msize**作業：

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

當指定 _CRTDBG_CHECK_ALWAYS_DF 時，會忽略*newFlag*參數的上16位。 在此情況下，每次您呼叫**malloc**、 **realloc**、 **free**和 **_msize**時，就會呼叫 **_CrtCheckMemory** 。

*newFlag*是要套用至 **_crtDbgFlag**的新狀態，而且是每個位欄位的值組合。

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>變更一個或多個位元欄位並建立旗標的新狀態

1. 使用*newFlag*等於 **_CRTDBG_REPORT_FLAG**的呼叫 **_CrtSetDbgFlag** ，以取得目前的 **_crtDbgFlag**狀態，並將傳回的值儲存在暫存變數中。

1. 使用相對應的位元遮罩（在應用程式代碼中以資訊清單常數表示），透過的位**或**暫存變數來開啟任何位。

1. 使用 **AND** 將變數與適當位元遮罩的位元 **NOT** 結合，以關閉其他位元。

1. 呼叫 **_CrtSetDbgFlag** ， *newFlag*等於儲存在暫存變數中的值，以設定 **_crtDbgFlag**的新狀態。

下列程式碼示範如何藉由將釋出的記憶體區塊保留在堆積的連結清單中，避免在每個配置要求中呼叫 **_CrtCheckMemory** ，以模擬低記憶體的狀況：

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

如需記憶體管理及偵錯堆積的概觀，請參閱 [CRT 偵錯堆積詳細資料](/visualstudio/debugger/crt-debug-heap-details)。

若要使用 **_CrtSetDbgFlag**函式停用旗標，您應該是 **，而**變數則是位元遮罩的位**NOT** 。

如果*newFlag*不是有效的值，此函式會叫用不正確參數處理常式，如[參數驗證](../../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，此函式會將**errno**設定為**EINVAL** ，並傳回 **_crtDbgFlag**的先前狀態。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

僅限偵錯版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example"></a>範例

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>另請參閱

[偵錯常式](../../c-runtime-library/debug-routines.md)<br/>
[_CRTDBG_CHECK_CRT_DF](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
