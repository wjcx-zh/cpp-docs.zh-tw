---
title: "exit、_Exit、_exit | Microsoft Docs"
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs: C++
helpviewer_keywords:
- exit function
- _exit function
- processes, terminating
- function calls, terminating
- process termination, calling
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: dbb54b756363da2069bbc4bface4e971fcab91e4
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/05/2018
---
# <a name="exit-exit-exit"></a>exit, _Exit, _exit

終止呼叫處理序。 `exit` 函式會在清除之後終止該處理序； `_exit` 及 `_Exit` 會立即予以終止。

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

_status_  
結束狀態碼。

## <a name="remarks"></a>備註

`exit`、 `_Exit` 及 `_exit` 函式會終止呼叫處理序。 `exit` 函式會呼叫執行緒區域物件的解構函式，接著再以後進先出 (LIFO) 順序呼叫 `atexit` 及 `_onexit`註冊的函式，最後在終止處理序之前，先排清所有檔案緩衝區。 `_Exit` 及 `_exit` 函式在終止處理程序時，不會終結執行緒區域物件或終止處理 `atexit` 或 `_onexit` 函式，也不會排清資料流緩衝區。

雖然`exit`，`_Exit`和`_exit`呼叫不會傳回一個值，在值_狀態_開放給主機環境或等待呼叫處理序，如果有的話，處理序結束之後。 一般而言，呼叫端組_狀態_值設為 0 表示正常結束，或設為其他值表示錯誤。 _狀態_值可供作業系統批次命令`ERRORLEVEL`而由兩個常數之一： `EXIT_SUCCESS`，值為 0，表示或`EXIT_FAILURE`，用來表示的值為 1。

`exit`、 `_Exit`、 `_exit`、 `quick_exit`、 `_cexit`及 `_c_exit` 函式的行為如下所示。

|功能|描述|
|--------------|-----------------|
|`exit`|執行完整的 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|`_Exit`|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|`_exit`|執行基本 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|`quick_exit`|執行快速 C 程式庫終止程序，再終止處理序，然後將所提供的狀態碼提供給主機環境。|
|`_cexit`|執行完整的 C 程式庫終止程序，然後傳回給呼叫端。 不會終止處理序。|
|`_c_exit`|執行基本的 C 程序庫終止程序，然後傳回給呼叫端。 不會終止處理序。|

當您呼叫 `exit`、  `_Exit` 或 `_exit` 函式時，任何在呼叫時即已存在之暫存或自動物件的解構函式皆不會予以呼叫。 自動物件是在函式中定義的非靜態本機的物件。 暫存物件是編譯器，例如函式呼叫所傳回的值所建立的物件。 若要呼叫之前先終結自動物件`exit`， `_Exit`，或`_exit`，請明確呼叫解構函式物件，如下所示：

```cpp
void last_fn() {}
    struct SomeClass {} myInstance{};
    // ...
    myInstance.~SomeClass(); // explicit destructor call
    exit(0);
}
```

請勿使用 `DLL_PROCESS_ATTACH` 從 `exit` 呼叫 `DllMain`。 若要結束`DLLMain`函式中，傳回`FALSE`從`DLL_PROCESS_ATTACH`。

## <a name="requirements"></a>需求

|功能|必要的標頭|
|--------------|---------------------|
|`exit`, `_Exit`, `_exit`|\<process.h> 或 \<stdlib.h>|

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

## <a name="see-also"></a>請參閱

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)  
[abort](../../c-runtime-library/reference/abort.md)  
[atexit](../../c-runtime-library/reference/atexit.md)  
[_cexit、_c_exit](../../c-runtime-library/reference/cexit-c-exit.md)  
[_exec、_wexec 函式](../../c-runtime-library/exec-wexec-functions.md)  
[_onexit、_onexit_m](../../c-runtime-library/reference/onexit-onexit-m.md)  
[quick_exit](../../c-runtime-library/reference/quick-exit1.md)  
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)  
[system、_wsystem](../../c-runtime-library/reference/system-wsystem.md)  
