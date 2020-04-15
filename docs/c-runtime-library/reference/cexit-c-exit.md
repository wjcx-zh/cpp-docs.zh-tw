---
title: _cexit、_c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333536"
---
# <a name="_cexit-_c_exit"></a>_cexit、_c_exit

執行清除作業，並傳回而不終止處理序。

## <a name="syntax"></a>語法

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>備註

**_cexit**函數按最後一名、先出 (LIFO) 順序調用由**exit**和 **_onexit**註冊的函數。 然後 **_cexit**刷新所有 I/O 緩衝區,並在返回之前關閉所有打開的流。 **_c_exit**與 **_exit**相同,但返回到調用進程,而不處理**exit**或 **_onexit**或刷新流緩衝區。 **退出****、_exit、_cexit****_cexit**和_c_exit 的行為顯示 **_c_exit**在下表 中。

|函式|行為|
|--------------|--------------|
|**離開**|執行完整的 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_exit**|執行快速 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_cexit**|執行完整的 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|
|**_c_exit**|執行快速 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|

調用 **_cexit**或 **_c_exit**函數時,不會調用調用時存在的任何臨時或自動物件的析構函數。 自動物件定義於未將物件宣告成靜態的函式中。 暫存物件是編譯器所建立的物件。 要在調用 **_cexit**或 **_c_exit**之前銷毀自動物件,請顯式調用該物件的析構函數,如下所示:

```cpp
myObject.myClass::~myClass( );
```

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
