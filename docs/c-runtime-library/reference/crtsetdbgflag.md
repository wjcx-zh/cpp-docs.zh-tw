---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
apiname:
- _CrtSetDbgFlag
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
ms.openlocfilehash: dcb8e37090e4c15ba849e76ca1cb1cc646a7bcc0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62348181"
---
# <a name="crtsetdbgflag"></a>_CrtSetDbgFlag

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

**_CrtSetDbgFlag**函式可讓應用程式，以控制偵錯堆積管理員如何追蹤記憶體配置藉由修改的位元欄位 **_crtDbgFlag**旗標。 應用程式可透過設定位元 (開啟)，指示偵錯堆積管理員執行特定偵錯作業，包含在應用程式結束時檢查記憶體遺漏並在發現任何問題時進行回報，以及藉由指定已釋放的記憶體區塊應保留在堆積的連結清單中來模擬低記憶體的情況，還有在每次配置要求時透過檢查每個記憶體區塊來驗證堆積的完整性。 當[_DEBUG](../../c-runtime-library/debug.md)未定義，呼叫 **_CrtSetDbgFlag**會在前置處理期間移除。

下表列出 **_crtDbgFlag** 的位元欄位，並描述它們的行為。 因為設定位元會導致增加診斷輸出，並降低程式執行速度，所以預設不會設定這些位元 (關閉)。 如需這些位元欄位的詳細資訊，請參閱[堆積狀態報告函式](/visualstudio/debugger/crt-debug-heap-details)。

|位元欄位|預設|描述|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|ON|ON:啟用偵錯堆積配置，並使用的記憶體區塊類型識別項，例如 **_CLIENT_BLOCK**。 OFF:新增配置至堆積的連結清單，但將區塊類型 **_IGNORE_BLOCK**。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|ON:呼叫[_CrtCheckMemory](crtcheckmemory.md)在每次配置和解除配置要求。 OFF: **_CrtCheckMemory**必須明確呼叫。<br /><br /> 堆積頻率檢查巨集會在設定此旗標時沒有效果。|
|**_CRTDBG_CHECK_CRT_DF**|OFF|ON:包含 **_CRT_BLOCK**類型在流失偵測和記憶體狀態差異作業。 OFF:執行階段程式庫內部使用的記憶體會忽略這些作業。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|ON:將釋放的記憶體區塊保留在堆積的連結清單，為它們指派 **_FREE_BLOCK**類型，而且它們填入位元組值 0xDD。 OFF:不要將釋放的區塊保留在堆積的連結清單。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|ON:執行自動流失檢查在程式結束時，透過呼叫[_CrtDumpMemoryLeaks](crtdumpmemoryleaks.md)並產生錯誤報表，如果應用程式無法釋放其配置的所有記憶體。 OFF:不要自動執行遺漏檢查在程式結束。<br /><br /> 也可以與任何堆積頻率檢查巨集結合。|

**堆積檢查頻率巨集**

您可以指定 C 執行階段程式庫執行偵錯堆積驗證的頻率 (**_CrtCheckMemory**) 為基礎的呼叫次數**malloc**， **realloc**， **免費**，並 **_msize**。

**_CrtSetDbgFlag**接著會檢查的上層 16 位元*newFlag*參數的值。 指定的值是數目**malloc**， **realloc**，**免費**，以及 **_msize**呼叫之間 **_CrtCheckMemory**呼叫。 針對此用途有四個預先定義的巨集。

|巨集|_CrtCheckMemory 呼叫之間，呼叫 malloc、realloc、free 及 _msize 的次數|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (根據預設沒有檢查任何堆積)|

根據預設， **_CrtCheckMemory**每 1,024 次呼叫**malloc**， **realloc**，**免費**，和 **_msize**。

例如，您可以在其中指定堆積檢查每個 16 **malloc**， **realloc**，**免費**，以及 **_msize**為下列程式碼的作業：

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

上層 16 位元*newFlag*指定 _CRTDBG_CHECK_ALWAYS_DF 時，會忽略參數。 在此情況下， **_CrtCheckMemory**稱為每次呼叫**malloc**， **realloc**，**免費**，和 **_msize**.

*newFlag*就會套用至新的狀態 **_crtDbgFlag**而為位元欄位的每個值的組合。

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>變更一個或多個位元欄位並建立旗標的新狀態

1. 呼叫 **_CrtSetDbgFlag**具有*newFlag*等於 **_CRTDBG_REPORT_FLAG**若要取得目前 **_crtDbgFlag**狀態，並儲存傳回在暫存變數的值。

1. 開啟任何位元的位元**或**的暫存變數和對應的位元遮罩 （由應用程式程式碼中的資訊清單常數）。

1. 使用 **AND** 將變數與適當位元遮罩的位元 **NOT** 結合，以關閉其他位元。

1. 呼叫 **_CrtSetDbgFlag**具有*newFlag*要設定的新狀態的暫存變數中儲存的值等於 **_crtDbgFlag**。

下列程式碼示範如何模擬低記憶體釋放堆積的連結清單中的記憶體區塊保留的條件，並防止 **_CrtCheckMemory**呼叫在每次配置要求：

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

若要停用旗標 **_CrtSetDbgFlag**函式，您應該**AND**使用位元變數**不**的位元遮罩。

如果*newFlag*不是有效的值，這個函式會叫用無效參數處理常式中，如中所述[參數驗證](../../c-runtime-library/parameter-validation.md)。 如果允許繼續執行，此函式會將**errno**要**EINVAL** ，並傳回先前的狀態 **_crtDbgFlag**。

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
