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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 78675ef91c2ab68e18f6111b4908886017ae1f79
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82917152"
---
# <a name="_cexit-_c_exit"></a>_cexit、_c_exit

執行清除作業，並傳回而不終止處理序。

## <a name="syntax"></a>語法

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>備註

**_Cexit**函式會以後進先出（LIFO）順序呼叫**atexit**和 **_onexit**所註冊的函式。 然後 **_cexit**會排清所有 i/o 緩衝區，並在傳回之前關閉所有開啟的資料流程。 **_c_exit**與 **_exit**相同，但會回到呼叫進程，而不會處理**atexit**或 **_onexit**或排清資料流程緩衝區。 [結束]、[ **_exit**]、[ **_cexit**] 和 [ **_c_exit** **] 的行為**如下表所示。

|函式|行為|
|--------------|--------------|
|**exit**|執行完整的 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_exit**|執行快速 C 程式庫終止程序，並終止處理序，然後因提供的狀態碼而結束。|
|**_cexit**|執行完整的 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|
|**_c_exit**|執行快速 C 程式庫終止程序，並傳回給呼叫端，但不終止處理序。|

當您呼叫 **_cexit**或 **_c_exit**函式時，不會呼叫存在於呼叫時的任何暫存或自動物件的析構函式。 自動物件定義於未將物件宣告成靜態的函式中。 暫存物件是編譯器所建立的物件。 若要在呼叫 **_cexit**或 **_c_exit**之前終結自動物件，請明確呼叫物件的析構函式，如下所示：

```cpp
myObject.myClass::~myClass( );
```

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
