---
title: _cwait
ms.date: 4/2/2020
api_name:
- _cwait
- _o__cwait
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
- api-ms-win-crt-process-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _cwait
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
ms.openlocfilehash: d54f62c8ce391b2c8ead92a0a73ac48e6f2b3cb3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348156"
---
# <a name="_cwait"></a>_cwait

等到其他處理序終止為止。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
intptr_t _cwait(
   int *termstat,
   intptr_t procHandle,
   int action
);
```

### <a name="parameters"></a>參數

*術語統計*<br/>
指定指定程序的程式碼的緩衝區的指標,或**NULL**。

*普羅克漢德爾*<br/>
要等待的進程的句柄(即,在 **_cwait**可以返回之前必須終止的進程)。

*action*<br/>
NULL:被 Windows 操作系統應用程式忽略;對於其他應用程式:要在*procHandle*上執行的操作代碼。

## <a name="return-value"></a>傳回值

當指定的進程成功完成時,返回指定進程的句柄,並將*術語統計*到指定進程返回的結果代碼。 否則,返回 -1 並設置**errno,** 如下所示。

|值|描述|
|-----------|-----------------|
|**ECHILD**|不存在指定的進程,*行程*無效,或者對[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)或[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API 的調用失敗。|
|**埃因瓦爾**|*操作*無效。|

有關這些代碼和其他返回代碼的詳細資訊,請參閱[errno、_doserrno、_sys_errlist和_sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_cwait**函數等待*進程提供的*指定進程的進程 ID 的終止。 傳遞給 **_cwait**的*procHandle*值應該是調用創建指定進程的[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函數返回的值。 如果在調用 **_cwait**之前進程 ID 終止 **,_cwait**立即返回。 **_cwait**可用於任何進程以等待存在有效句柄 *(procHandle)* 的任何其他已知進程。

*術語統計*指向將存儲指定進程的返回代碼的緩衝區。 *術語統計值*指示指定進程是否通過調用 Windows [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) API 正常終止。 如果指定的行程呼叫**退出**或 **_exit、** 從**main**返回或到達**主**的末尾,則內部調用**ExitProcess。** 有關通過*此字串統計表*傳回的值的詳細資訊,請參閱[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)。 如果使用*術語統計*的**NULL**值呼叫 **_cwait,** 則不儲存指定行程的傳回代碼。

Windows 作業系統將忽略*操作*參數,因為在這些環境中未實現父子關係。

除非*行程處理*是 -1 或 -2(對當前進程或線程的句柄),否則句柄將關閉。 因此，在此情況中，請勿使用傳回的處理常式。

默認情況下,此函數的全域狀態範圍為應用程式。 要改變此情況,請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="example"></a>範例

```C
// crt_cwait.c
// compile with: /c
// This program launches several processes and waits
// for a specified process to finish.

#define _CRT_RAND_S

#include <windows.h>
#include <process.h>
#include <stdlib.h>
#include <stdio.h>
#include <time.h>

// Macro to get a random integer within a specified range
#define getrandom( min, max ) (( (rand_s (&number), number) % (int)((( max ) + 1 ) - ( min ))) + ( min ))

struct PROCESS
{
   int     nPid;
   char    name[40];
} process[4] = { { 0, "Ann" }, { 0, "Beth" }, { 0, "Carl" }, { 0, "Dave" } };

int main( int argc, char *argv[] )
{
   int termstat, c;
   unsigned int number;

   srand( (unsigned)time( NULL ) );    // Seed randomizer

   // If no arguments, this is the calling process
   if ( argc == 1 )
   {
      // Spawn processes in numeric order
      for ( c = 0; c < 4; c++ ) {
         _flushall();
         process[c].nPid = _spawnl( _P_NOWAIT, argv[0], argv[0],
                                    process[c].name, NULL );
      }

      // Wait for randomly specified process, and respond when done
      c = getrandom( 0, 3 );
      printf( "Come here, %s.\n", process[c].name );
      _cwait( &termstat, process[c].nPid, _WAIT_CHILD );
      printf( "Thank you, %s.\n", process[c].name );

   }
   // If there are arguments, this must be a spawned process
   else
   {
      // Delay for a period that's determined by process number
      Sleep( (argv[1][0] - 'A' + 1) * 1000L );
      printf( "Hi, Dad. It's %s.\n", argv[1] );
   }
}
```

```Output
Hi, Dad. It's Ann.
Come here, Ann.
Thank you, Ann.
Hi, Dad. It's Beth.
Hi, Dad. It's Carl.
Hi, Dad. It's Dave.
```

## <a name="see-also"></a>另請參閱

[處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
