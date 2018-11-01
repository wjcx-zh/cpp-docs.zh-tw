---
title: exit, _Exit, _exit
ms.date: 1/02/2018
apiname:
- _exit
- exit
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
- Exit
- _exit
- process/exit
- process/_Exit
- stdlib/exit
- stdlib/_Exit
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
ms.openlocfilehash: 7b2a22649d779f382bb4055b1e44c14312627ccd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50451749"
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

終止呼叫處理序。 **結束**函式會將其終止後清除;**_exit**並 **_Exit**立即予以終止。

> [!NOTE]
> 請勿使用這個方法關閉通用 Windows 平台 (UWP) 應用程式中，除了測試或偵錯案例。 以程式設計或 UI 方式關閉對市集應用程式不允許根據[Microsoft Store 原則](/legal/windows/agreements/store-policies)。 如需詳細資訊，請參閱 < [UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。 如需 Windows 10 應用程式的詳細資訊，請參閱 [Windows 10 app 使用方法指南](https://developer.microsoft.com/windows/apps)。

## <a name="syntax"></a>語法

```C
void exit(
   int const status
);
void _Exit(
   int const status
);
void _exit(
   int const status
);
```

### <a name="parameters"></a>參數

*status*<br/>
結束狀態碼。

## <a name="remarks"></a>備註

**結束**， **_Exit**並 **_exit**函式會終止呼叫處理序。 **結束**函式會呼叫解構函式的執行緒區域物件，然後呼叫 — 後進先出 (LIFO) 順序，會註冊的函式**atexit**和 **_onexit**，並終止處理程序前，然後排清所有檔案緩衝區。 **_Exit**並 **_exit**函式會終止處理程序，而不會終結執行緒區域物件或處理**atexit**或 **_onexit**函式，並不會排清資料流緩衝區。

雖然**結束**， **_Exit**並 **_exit**呼叫不會傳回一個值，在值*狀態*開放給主機環境或者，如果有的話，程序結束之後等待呼叫處理序。 一般而言，呼叫端組*狀態*值 0，表示正常結束，或一些其他值，以表示發生錯誤。 *狀態*值可供作業系統批次命令**ERRORLEVEL**和兩個常數之一代表： **EXIT_SUCCESS**，代表值為 0，或**EXIT_FAILURE**，用來表示的值為 1。

**結束**， **_Exit**， **_exit**， **quick_exit**， **_cexit**，以及 **_c_exit**函式的行為，如下所示。

|功能|描述|
|--------------|-----------------|
|**exit**|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_Exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**quick_exit**|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_cexit**|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|
|**_c_exit**|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|

當您呼叫**結束**， **_Exit**或是 **_exit**函式，在呼叫時存在的任何暫存或自動物件的解構函式不會呼叫。 自動物件是定義在函式的非靜態本機物件。 暫存物件是由編譯器，例如函式呼叫所傳回的值建立的物件。 要終結自動物件，然後再呼叫**結束**， **_Exit**，或 **_exit**、 明確呼叫解構函式物件，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

請勿使用**DLL_PROCESS_ATTACH**來呼叫**結束**從**DllMain**。 若要結束**DLLMain**函式中，傳回**FALSE**從**DLL_PROCESS_ATTACH**。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|**結束**， **_Exit**， **_exit**|\<process.h> 或 \<stdlib.h>|

如需其他相容性資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_exit.c
// This program returns an exit code of 1. The
// error code could be tested in a batch file.

#include <stdlib.h>

int main( void )
{
   exit( 1 );
}
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit、_c_exit](cexit-c-exit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
