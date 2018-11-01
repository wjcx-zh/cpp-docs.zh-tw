---
title: _cexit、_c_exit
ms.date: 11/04/2016
apiname:
- _c_exit
- _cexit
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
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
ms.openlocfilehash: a075e8a8e965a195765b86ffa21fed0915dbf5ab
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495130"
---
# <a name="cexit-cexit"></a>_cexit、_c_exit

執行清除作業，並傳回而不終止處理序。

## <a name="syntax"></a>語法

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>備註

**_Cexit**函式呼叫，在後進先出 (LIFO) 順序、 註冊的函式**atexit**並 **_onexit**。 然後 **_cexit**清除所有 I/O 緩衝區，並傳回之前關閉所有開啟的資料流。 **_c_exit**相同 **_exit**但傳回到呼叫的處理序，而不處理**atexit**或是 **_onexit**或排清資料流緩衝區。 行為**結束**， **_exit**， **_cexit**，以及 **_c_exit**下表所示。

|功能|行為|
|--------------|--------------|
|**exit**|執行完整的 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_exit**|執行快速 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_cexit**|執行完整的 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|
|**_c_exit**|執行快速 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|

當您呼叫 **_cexit**或是 **_c_exit**函式呼叫時存在的任何暫存或自動物件的解構函式不會呼叫。 自動物件定義於未將物件宣告成靜態的函式中。 暫存物件是編譯器所建立的物件。 要終結自動物件，再呼叫 **_cexit**或 **_c_exit**、 明確呼叫解構函式物件，如下：

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](exit-exit-exit.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
