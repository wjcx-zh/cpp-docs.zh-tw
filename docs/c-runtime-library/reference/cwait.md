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
- api-ms-win-crt-private-l1-1-0.dll
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
ms.openlocfilehash: 9e2e23acb041004b9e96d1c6558ae195ed522155
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82914788"
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

*termstat*<br/>
緩衝區的指標，其中會儲存指定之處理常式的結果碼，或為**Null**。

*procHandle*<br/>
要等候之進程的控制碼（也就是必須在 **_cwait**可以傳回之前終止的進程）。

*action*<br/>
Null： Windows 作業系統應用程式已忽略;針對其他應用程式：要在*procHandle*上執行的動作程式碼。

## <a name="return-value"></a>傳回值

當指定的進程成功完成時，會傳回指定之進程的控制碼，並將*termstat*設定為指定之進程所傳回的結果碼。 否則，會傳回-1，並設定**errno** ，如下所示。

|值|描述|
|-----------|-----------------|
|**ECHILD**|沒有指定的進程存在、 *procHandle*無效，或呼叫[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)或[WaitForSingleObject](/windows/win32/api/synchapi/nf-synchapi-waitforsingleobject) API 失敗。|
|**EINVAL**|*動作*無效。|

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Cwait**函式會等候*procHandle*所提供之指定進程的處理序識別碼終止。 傳遞給 **_cwait**的*procHandle*值應該是呼叫建立指定進程的[_spawn](../../c-runtime-library/spawn-wspawn-functions.md)函數所傳回的值。 如果在呼叫 **_cwait**之前，處理序識別碼終止， **_cwait**會立即傳回。 **_cwait**可以由任何進程用來等候任何其他已知的進程（有有效的控制碼（*procHandle*））。

*termstat*會指向緩衝區，其中會儲存指定之進程的傳回碼。 *Termstat*的值會指出指定的進程是否正常終止，方法是呼叫 Windows [ExitProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitprocess) API。 如果指定的進程呼叫**exit**或 **_exit**、從**main**傳回，或到達**main**結尾，就會在內部呼叫**ExitProcess** 。 如需透過*termstat*傳回之值的詳細資訊，請參閱[GetExitCodeProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodeprocess)。 如果使用*termstat*的**Null**值呼叫 **_cwait** ，則不會儲存指定之進程的傳回碼。

Windows 作業系統會忽略*action*參數，因為這些環境中不會實作為父子式關聯性。

除非*procHandle*是-1 或-2 （對目前進程或執行緒的控制碼），否則控制碼將會關閉。 因此，在此情況中，請勿使用傳回的處理常式。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

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
