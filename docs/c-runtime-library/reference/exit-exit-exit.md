---
title: exit、_Exit、_exit | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb62c18f7508a21e24fb5628e8ac01162db1405e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

終止呼叫處理序。 **結束**函式會將它結束之後清除。**_exit**和 **_Exit**會立即予以終止。

> [!NOTE]
> 請勿使用這個方法關閉通用 Windows 平台 (UWP) 應用程式中，除了測試或偵錯案例。 透過程式設計或 UI 兩種方式關閉市集應用程式不允許根據[Microsoft 市集原則](/legal/windows/agreements/store-policies)。 如需詳細資訊，請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。 如需 Windows 10 應用程式的詳細資訊，請參閱 [Windows 10 app 使用方法指南](http://go.microsoft.com/fwlink/p/?linkid=619133)。

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

*狀態*結束狀態碼。

## <a name="remarks"></a>備註

**結束**， **_Exit**和 **_exit**函式會終止呼叫處理序。 **結束**函式呼叫解構函式的執行緒區域物件，然後呼叫 — 後進先出 (LIFO) 順序 — 函式所登錄的**atexit**和 **_onexit**，和它所終止處理程序之前，然後清除所有檔案緩衝區。 **_Exit**和 **_exit**函式會終止處理程序不會終結執行緒區域物件或處理**atexit**或 **_onexit**函式，並不會排清資料流緩衝區。

雖然**結束**， **_Exit**和 **_exit**呼叫不會傳回一個值，在值*狀態*開放給主機環境或者，如果有的話，處理序結束之後等待呼叫處理序。 一般而言，呼叫端組*狀態*值設為 0 表示正常結束，或設為其他值表示錯誤。 *狀態*值可供作業系統批次命令**ERRORLEVEL**而由兩個常數之一： **EXIT_SUCCESS**，代表值0，或**EXIT_FAILURE**，用來表示的值為 1。

**結束**， **_Exit**， **_exit**， **quick_exit**， **_cexit**，和 **_c_exit**函式的行為，如下所示。

|功能|描述|
|--------------|-----------------|
|**exit**|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_Exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**quick_exit**|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_cexit**|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|
|**_c_exit**|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|

當您呼叫**結束**， **_Exit**或 **_exit**函式，在呼叫時存在的任何暫存或自動物件的解構函式不會呼叫。 自動物件是在函式中定義的非靜態本機的物件。 暫存物件是編譯器，例如函式呼叫所傳回的值所建立的物件。 若要呼叫之前先終結自動物件**結束**， **_Exit**，或 **_exit**，請明確呼叫解構函式物件，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

請勿使用**DLL_PROCESS_ATTACH**呼叫**結束**從**DllMain**。 若要結束**DLLMain**函式中，傳回**FALSE**從**DLL_PROCESS_ATTACH**。

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
