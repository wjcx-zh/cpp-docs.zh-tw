---
title: _cwait | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 8d5cfdb53b5aab8e6b0404b84de87ba24ee57597
ms.contentlocale: zh-tw
ms.lasthandoff: 04/01/2017

---
# <a name="cwait"></a>_cwait
等到其他處理序終止為止。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
intptr_t _cwait(   
   int *termstat,  
   intptr_t procHandle,  
   int action   
);  
```  
  
#### <a name="parameters"></a>參數  
 `termstat`  
 緩衝區 (其中要儲存指定處理序的結果碼) 的指標，或為 NULL。  
  
 `procHandle`  
 要等待之處理序的處理常式 (也就是說，該處理序必須先終止，才能傳回 `_cwait`)。  
  
 `action`  
 NULL：會由 Windows 作業系統應用程式忽略；對於其他應用程式：要執行於 `procHandle` 的動作碼。  
  
## <a name="return-value"></a>傳回值  
 當指定處理序成功完成時，會傳回指定處理序的處理常式，並將 `termstat` 設定為指定處理序傳回的結果碼。 否則，傳回-1，並設定`errno`，如下所示。  
  
|值|說明|  
|-----------|-----------------|  
|`ECHILD`|指定處理序不存在、`procHandle` 無效，或是呼叫 [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx) 或 [WaitForSingleObject](http://msdn.microsoft.com/library/windows/desktop/ms687032.aspx) API 失敗。|  
|`EINVAL`|`action` 無效。|  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_cwait` 函式會等待 `procHandle` 所提供之指定處理序的處理序識別碼終止。 `procHandle` 的值 (傳遞至 `_cwait`) 應為建立指定處理序時呼叫 [_spawn](../../c-runtime-library/spawn-wspawn-functions.md) 函式所傳回的值。 若處理序識別碼在呼叫 `_cwait` 之前終止，則會立即傳回 `_cwait`。 `_cwait` 可供所有處理序用於等待其他所有已知處理序 (其中有有效的處理常式 `procHandle`)。  
  
 `termstat` 指出要儲存指定處理序的傳回碼的緩衝區。 `termstat` 的值指出指定的處理序是否正常地經由呼叫 Windows [ExitProcess](http://msdn.microsoft.com/library/windows/desktop/ms682658.aspx) API 來終止。 若指定處理序呼叫 `ExitProcess` 或 `exit` (從 `_exit` 傳回，或達到 `main` 的結尾) 時，會從內部呼叫 `main`。 如需透過 `termstat` 傳回之值的詳細資訊，請參閱 [GetExitCodeProcess](http://msdn.microsoft.com/library/windows/desktop/ms683189.aspx)。 若 `_cwait` 是透過使用 `termstat` 的 NULL 值所呼叫，則不會儲存指定處理序的傳回碼。  
  
 `action` 參數是由 Windows 作業系統忽略，因為不會在這些環境中實作父子關係。  
  
 除非 `procHandle` 為 -1 或 -2 (目前處理序或執行緒的處理常式)，否則會關閉處理常式。 因此，在此情況中，請勿使用傳回的處理常式。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_cwait`|\<process.h>|\<errno.h>|  
  
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
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_spawn、_wspawn 函式](../../c-runtime-library/spawn-wspawn-functions.md)
