---
title: _cwait | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- _cwait
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
- api-ms-win-crt-process-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _cwait
dev_langs:
- C++
helpviewer_keywords:
- cwait function
- _cwait function
ms.assetid: d9b596b5-45f4-4e03-9896-3f383cb922b8
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ef1e3c2566c9ee8628f077c11e7987f27dfb51d5
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2018
---
# <a name="cwait"></a>_cwait

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

*termstat*<br/>
緩衝區 (其中要儲存指定處理序的結果碼) 的指標，或為 NULL。

*procHandle*<br/>
等候處理序控制代碼 (也就是說，必須先終止處理序 **_cwait**可以傳回)。

*action*<br/>
NULL： 會忽略由 Windows 作業系統應用程式。對於其他應用程式： 上執行的動作碼*procHandle*。

## <a name="return-value"></a>傳回值

指定的處理序已順利完成，傳回指定之處理序控制代碼，並設定*termstat*指定的處理序所傳回的結果碼。 否則，傳回-1，並設定**errno** ，如下所示。

|值|描述|
|-----------|-----------------|
|**ECHILD**|指定處理序不存在， *procHandle*無效，或是呼叫[GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx)或[WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) API 失敗。|
|**EINVAL**|*動作*無效。|

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Cwait**函式會等候所提供的程序識別碼指定之處理序終止*procHandle*。 值*procHandle*傳遞至 **_cwait**應該呼叫所傳回的值[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函式，建立指定的處理序。 如果處理序識別碼終止之前 **_cwait**呼叫時， **_cwait**會立即傳回。 **_cwait**可供所有處理序等待其他所有已知處理序，其有效的控制代碼 (*procHandle*) 存在。

*termstat*指向要儲存指定處理序的傳回碼的緩衝區。 值*termstat*指出指定的處理序正常終止經由呼叫 Windows [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx)應用程式開發介面。 **ExitProcess**如果指定的處理序呼叫在內部呼叫**結束**或 **_exit**，從傳回**主要**，或達到結尾**主要**. 如需有關的值，就會傳遞回*termstat*，請參閱[GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx)。 如果 **_cwait**呼叫使用 NULL 值的*termstat*，不會儲存指定處理序的傳回碼。

*動作*參數已忽略由 Windows 作業系統，因為這些環境中不會實作父子式關聯性。

除非*procHandle*為-1 或-2 （控制代碼對應到目前的處理序或執行緒），將會關閉這個控制代碼。 因此，在此情況中，請勿使用傳回的處理常式。

## <a name="requirements"></a>需求

|常式|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_cwait**|\<process.h>|\<errno.h>|

如需相容性的詳細資訊，請參閱 [相容性](../../c-runtime-library/compatibility.md)。

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

[流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
