---
title: exit, _Exit, _exit
ms.date: 01/02/2018
api_name:
- _exit
- exit
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
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: fd988ca6339c00b454d673d3bec6f137753ac83a
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941661"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

終止呼叫處理序。 **Exit**函式會在清除之後終止它; **_exit**和 **_exit**會立即將其終止。

> [!NOTE]
> 請勿使用此方法來關閉通用 Windows 平臺（UWP）應用程式，但不包括測試或偵測案例。 根據[Microsoft Store 的原則](/legal/windows/agreements/store-policies)，不允許以程式設計或 UI 方式關閉存放區應用程式。 如需詳細資訊，請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。 如需 Windows 10 應用程式的詳細資訊，請參閱 [Windows 10 app 使用方法指南](https://developer.microsoft.com/windows/apps)。

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

**Exit**、 **_Exit**和 **_Exit**函式會結束通話進程。 **Exit**函數會呼叫執行緒區域物件的析構函式，然後以後進先出（LIFO）順序呼叫**atexit**和 **_onexit**所註冊的函式，然後在結束之前清除所有檔案緩衝區流程. **_Exit**和 **_Exit**函式會終止進程，而不會終結執行緒區域物件或處理**atexit**或 **_onexit**函數，而不會排清資料流程緩衝區。

雖然**exit**、 **_Exit**和 **_Exit**呼叫不會傳回值，但在進程結束之後，*狀態*中的值會提供給主機環境或等候呼叫進程（如果有的話）。 一般來說，呼叫者會將*狀態值*設定為0，以表示正常結束，或設為其他值來表示錯誤。 *狀態*值可供作業系統批次命令**ERRORLEVEL**使用，並以兩個常數的其中一個來表示：**EXIT_SUCCESS**，代表0的值或**EXIT_FAILURE**，代表1的值。

**Exit**、 **_Exit**、 **_Exit**、 **quick_exit**、 **_cexit**和 **_c_exit**函數的行為如下所示。

|函數|描述|
|--------------|-----------------|
|**exit**|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_Exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**quick_exit**|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_cexit**|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|
|**_c_exit**|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|

當您呼叫**exit**、 **_Exit**或 **_Exit**函式時，不會呼叫存在於呼叫時的任何暫存或自動物件的析構函數。 自動物件是在函數中定義的非靜態本機物件。 暫存物件是編譯器所建立的物件，例如函式呼叫所傳回的值。 若要在呼叫**exit**、 **_Exit**或 **_Exit**之前終結自動物件，請明確呼叫物件的析構函式，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

請勿使用**DLL_PROCESS_ATTACH**來呼叫**DllMain**的**exit** 。 若要結束**DLLMain**函數，請從**DLL_PROCESS_ATTACH**傳回**FALSE** 。

## <a name="requirements"></a>需求

|函數|必要的標頭|
|--------------|---------------------|
|**exit**、 **_Exit**、 **_Exit**|\<process.h> 或 \<stdlib.h>|

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
