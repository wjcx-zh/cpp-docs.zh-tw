---
title: exit, _Exit, _exit
ms.date: 4/2/2020
api_name:
- _exit
- exit
- _o__exit
- _o_exit
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
ms.openlocfilehash: 5bdb5ff5c8309e03a49f9518f65a45d5757e9bfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81347627"
---
# <a name="exit-_exit-_exit"></a>exit, _Exit, _exit

終止呼叫處理序。 **退出**函數在清理后終止它;**_exit,_Exit**立即終止。 **_Exit**

> [!NOTE]
> 除非在測試或調試方案中,否則不要使用此方法關閉通用 Windows 平臺 (UWP) 應用。 根據[Microsoft 應用商店策略](/legal/windows/agreements/store-policies),不允許以程式設計或 UI 方式關閉應用商店應用。 有關詳細資訊,請參閱[UWP 應用程式生命週期](/windows/uwp/launch-resume/app-lifecycle)。 如需 Windows 10 應用程式的詳細資訊，請參閱 [Windows 10 app 使用方法指南](https://developer.microsoft.com/windows/apps)。

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

*狀態*<br/>
結束狀態碼。

## <a name="remarks"></a>備註

**退出****、_Exit**和 **_exit**函數終止調用過程。 **退出**函數呼叫線程本地物件的析構函數,然後調用 -以先出後 (LIFO) 順序呼叫 - 透過**atexit**和 **_onexit**註冊的函數,然後在它終止行程之前刷新所有文件緩衝區。 **_Exit**和 **_exit**函數在不銷毀線程本地物件或處理**exit**或 **_onexit**函數的情況下終止進程,並且不刷新流緩衝區。

儘管**退出****、_Exit**和 **_exit**調用不會返回值,但*狀態*值在行程退出後將提供給主機環境或等待調用進程(如果存在)。 通常,調用方將*狀態*值設置為 0 以指示正常退出,或將另一些值設置以指示錯誤。 *狀態*值可用於作業系統批次處理命令**ERRORLEVEL,** 由兩個常量之一表示 **:EXIT_SUCCESS,** 表示值 0,或表示值 1 的**EXIT_FAILURE。**

**出口**、_Exit、_exit、quick_exit、_cexit **_cexit**和 **_c_exit**功能如下。 **_Exit** **_exit** **quick_exit**

|函式|描述|
|--------------|-----------------|
|**離開**|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_Exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_exit**|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**quick_exit**|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|**_cexit**|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|
|**_c_exit**|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|

調用**出口****、_Exit**或 **_exit**函數時,不會調用調用調用時存在的任何臨時或自動物件的析構函數。 自動物件是在函數中定義的非靜態局部物件。 臨時物件是由編譯器創建的物件,例如函數調用返回的值。 要在調用**退出****、_Exit**或 **_exit**之前銷毀自動物件,請顯式調用物件的析構函數,如下所示:

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

請勿使用**DLL_PROCESS_ATTACH**呼叫**DllMain****的離開**。 要退出**DLLMain**函數,從**DLL_PROCESS_ATTACH**返回**FALSE。**

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|函式|必要的標頭|
|--------------|---------------------|
|**出口**, **_Exit**, **_exit**|\<process.h> 或 \<stdlib.h>|

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

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_cexit、_c_exit](cexit-c-exit.md)<br/>
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)<br/>
[_onexit、_onexit_m](onexit-onexit-m.md)<br/>
[quick_exit](quick-exit1.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](system-wsystem.md)<br/>
