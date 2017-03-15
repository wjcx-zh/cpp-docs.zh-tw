---
title: _pipe | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _pipe
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
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- pipe
- _pipe
dev_langs:
- C++
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: 20
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 0e45008d3f55c11cfa7da2aa4db9ca1277a6f77f
ms.lasthandoff: 02/24/2017

---
# <a name="pipe"></a>_pipe
建立用於讀取和寫入的管道。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。 如需詳細資訊，請參閱 [/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## <a name="syntax"></a>語法  
  
```  
  
      int _pipe(  
int *pfds,  
unsigned int psize,  
int textmode   
);  
```  
  
#### <a name="parameters"></a>參數  
 `pfds`[2]  
 要保存讀取和寫入檔案描述項的陣列。  
  
 `psize`  
 要保留的記憶體數量。  
  
 `textmode`  
 檔案模式。  
  
## <a name="return-value"></a>傳回值  
 若成功，即傳回 0。 傳回 -1 以指出錯誤。 發生錯誤時，`errno` 會設定為下列其中一個值：  
  
-   `EMFILE`，表示沒有更多檔案描述項可用。  
  
-   `ENFILE`，表示系統檔案表溢位。  
  
-   `EINVAL`，表示陣列 `pfds` 為 null 指標，或傳入的 `textmode` 值無效。  
  
 如需這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## <a name="remarks"></a>備註  
 `_pipe` 函式會建立一個「管道」，這是某個程式將資訊傳遞至其他程式時所使用的人工 I/O 通道。 管道類似於檔案，因為它具有檔案指標及 (或) 檔案描述項，而且可以透過使用標準程式庫輸入和輸出函式從中讀取或寫入至其中。 不過，管道並不代表特定檔案或裝置。 相反地，它代表與程式本身記憶體無關，而且完全由作業系統控制之記憶體中的暫存位置。  
  
 `_pipe` 類似於 `_open`，但會開啟管道以供讀取和寫入，並傳回兩個檔案描述項而不是一個。 程式可以在管道兩端使用，或關閉不需要的一端。 例如，當 Windows 中的命令處理程式執行命令時 (例如 `PROGRAM1 | PROGRAM2`)，就會建立一個管道。  
  
 `PROGRAM1` 的標準輸出描述項會附加至管線的寫入描述項。 `PROGRAM2` 的標準輸入描述項會附加至管線的讀取描述項。 如此一來，就不需要建立暫存檔來將資訊傳遞至其他程式。  
  
 `_pipe` 函式會將兩個檔案描述項傳回至 `pfds` 引數中的管道。 元素 `pfds`[0] 包含讀取描述項，而元素 `pfds`[1] 包含寫入描述項。 管道檔案描述項的使用方式與其他檔案描述項相同 (低層級輸入和輸出函式 `_read` 和 `_write` 可以從管道讀取及寫入至管道)。若要偵測管道結束狀況，請檢查是否有傳回 0 作為讀取的位元組數目的 `_read` 要求。  
  
 `psize` 引數指定要保留給管道的記憶體數量 (以位元組為單位)。 `textmode` 引數指定管道的轉譯模式。 資訊清單常數 `_O_TEXT` 指定文字轉譯，而常數 `_O_BINARY` 指定二進位轉譯 (如需文字和二進位模式的說明，請參閱 [fopen、_wfopen](../../c-runtime-library/reference/fopen-wfopen.md))。如果 `textmode` 引數為 0，`_pipe` 會使用預設模式變數 [_fmode](../../c-runtime-library/fmode.md) 所指定的預設轉譯模式。  
  
 在多執行緒程式中，不會執行任何鎖定。 傳回的檔案描述項是新開啟的，必須完成 `_pipe` 呼叫，才能供任何執行緒參考。  
  
 若要使用 `_pipe` 函式在父處理序和子處理序之間進行通訊，每個處理序只能在管道上開啟一個描述項。 這兩個描述項必須相反：如果父系開啟讀取描述項，則子系就必須開啟寫入描述項。 要這樣做的最簡單方式就是使用 `textmode` 對 `_O_NOINHERIT` 旗標進行 `OR` (`|`)。 然後，使用 `_dup` 或 `_dup2` 建立您要傳遞至子系之管道描述項的可繼承複本。 關閉原始描述項，然後繁衍子處理序。 從繁衍呼叫傳回時，請關閉父處理序中重複的描述項。 如需詳細資訊，請參閱本文稍後的範例 2。  
  
 在 Windows 作業系統中，當管道的所有描述項都已關閉時，就會終結管道 (如果管道上的所有讀取描述項都已關閉，則寫入至管道會造成錯誤)。管道上的所有讀取和寫入作業會等到有足夠的資料或足夠的緩衝區空間，以完成 I/O 要求。  
  
## <a name="requirements"></a>需求  
  
|常式|必要的標頭|選擇性標頭|  
|-------------|---------------------|---------------------|  
|`_pipe`|\<io.h>|\<fcntl.h>1、\<errno.h>2|  
  
 1 適用於 `_O_BINARY` 和 `_O_TEXT` 定義。  
  
 2 `errno` 定義。  
  
 如需相容性的詳細資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## <a name="libraries"></a>程式庫  
 所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。  
  
## <a name="example-1"></a>範例 1  
  
```  
  
      // crt_pipe.c  
/* This program uses the _pipe function to pass streams of  
 * text to spawned processes.  
 */  
  
#include <stdlib.h>  
#include <stdio.h>  
#include <io.h>  
#include <fcntl.h>  
#include <process.h>  
#include <math.h>  
  
enum PIPES { READ, WRITE }; /* Constants 0 and 1 for READ and WRITE */  
#define NUMPROBLEM 8  
  
int main( int argc, char *argv[] )  
{  
  
   int fdpipe[2];  
   char hstr[20];  
   int pid, problem, c;  
   int termstat;  
  
   /* If no arguments, this is the spawning process */  
   if( argc == 1 )  
   {  
  
      setvbuf( stdout, NULL, _IONBF, 0 );  
  
      /* Open a set of pipes */  
      if( _pipe( fdpipe, 256, O_BINARY ) == -1 )  
          exit( 1 );  
  
      /* Convert pipe read descriptor to string and pass as argument   
       * to spawned program. Program spawns itself (argv[0]).  
       */  
      _itoa_s( fdpipe[READ], hstr, sizeof(hstr), 10 );  
      if( ( pid = _spawnl( P_NOWAIT, argv[0], argv[0],   
            hstr, NULL ) ) == -1 )  
          printf( "Spawn failed" );  
  
      /* Put problem in write pipe. Since spawned program is   
       * running simultaneously, first solutions may be done   
       * before last problem is given.  
       */  
      for( problem = 1000; problem <= NUMPROBLEM * 1000; problem += 1000)  
      {  
  
         printf( "Son, what is the square root of %d?\n", problem );  
         _write( fdpipe[WRITE], (char *)&problem, sizeof( int ) );  
  
      }  
  
      /* Wait until spawned program is done processing. */  
      _cwait( &termstat, pid, WAIT_CHILD );  
      if( termstat & 0x0 )  
         printf( "Child failed\n" );  
  
      _close( fdpipe[READ] );  
      _close( fdpipe[WRITE] );  
  
   }  
  
   /* If there is an argument, this must be the spawned process. */  
   else  
   {  
  
      /* Convert passed string descriptor to integer descriptor. */  
      fdpipe[READ] = atoi( argv[1] );  
  
      /* Read problem from pipe and calculate solution. */  
      for( c = 0; c < NUMPROBLEM; c++ )  
      {  
  
        _read( fdpipe[READ], (char *)&problem, sizeof( int ) );  
        printf( "Dad, the square root of %d is %3.2f.\n",  
                 problem, sqrt( ( double )problem ) );  
  
      }  
   }  
}  
```  
  
## <a name="sample-output"></a>範例輸出  
  
```  
Son, what is the square root of 1000?  
Son, what is the square root of 2000?  
Son, what iDad, the square root of 1000 is 31.62.  
Dad, the square root of 2000 is 44.72.  
s the square root of 3000?  
Dad, the square root of 3000 is 54.77.  
Son, what is the square root of 4000?  
Dad, the square root of 4000 is 63.25.  
Son, what is the square root of 5000?  
Dad, the square root of 5000 is 70.71.  
Son, what is the square root of 6000?  
SonDad, the square root of 6000 is 77.46.  
, what is the square root of 7000?  
Dad, the square root of 7000 is 83.67.  
Son, what is the square root of 8000?  
Dad, the square root of 8000 is 89.44.  
```  
  
## <a name="example-2"></a>範例 2  
 這是基本篩選應用程式。 它會在建立管道之後繁衍應用程式 crt_pipe_beeper，該管道會將所繁衍之應用程式的 stdout 引導至篩選。 此篩選會移除 ASCII 7 (Beep) 字元。  
  
```  
// crt_pipe_beeper.c  
  
#include <stdio.h>  
#include <string.h>  
  
int main()  
{  
   int   i;  
   for(i=0;i<10;++i)  
      {  
         printf("This is speaker beep number %d...\n\7", i+1);  
      }  
   return 0;  
}  
```  
  
 實際篩選應用程式：  
  
```  
// crt_pipe_BeepFilter.C  
// arguments: crt_pipe_beeper.exe  
  
#include <windows.h>  
#include <process.h>  
#include <memory.h>  
#include <string.h>  
#include <stdio.h>  
#include <fcntl.h>  
#include <io.h>  
  
#define   OUT_BUFF_SIZE 512  
#define   READ_FD 0  
#define   WRITE_FD 1  
#define   BEEP_CHAR 7  
  
char szBuffer[OUT_BUFF_SIZE];  
  
int Filter(char* szBuff, ULONG nSize, int nChar)  
{  
   char* szPos = szBuff + nSize -1;  
   char* szEnd = szPos;  
   int nRet = nSize;  
  
   while (szPos > szBuff)  
   {  
      if (*szPos == nChar)  
         {  
            memmove(szPos, szPos+1, szEnd - szPos);  
            --nRet;  
         }  
      --szPos;  
   }  
   return nRet;  
}  
  
int main(int argc, char** argv)  
{  
   int nExitCode = STILL_ACTIVE;  
   if (argc >= 2)  
   {  
      HANDLE hProcess;  
      int fdStdOut;  
      int fdStdOutPipe[2];  
  
      // Create the pipe  
      if(_pipe(fdStdOutPipe, 512, O_NOINHERIT) == -1)  
         return   1;  
  
      // Duplicate stdout file descriptor (next line will close original)  
      fdStdOut = _dup(_fileno(stdout));  
  
      // Duplicate write end of pipe to stdout file descriptor  
      if(_dup2(fdStdOutPipe[WRITE_FD], _fileno(stdout)) != 0)  
         return   2;  
  
      // Close original write end of pipe  
      _close(fdStdOutPipe[WRITE_FD]);  
  
      // Spawn process  
      hProcess = (HANDLE)_spawnvp(P_NOWAIT, argv[1],   
       (const char* const*)&argv[1]);  
  
      // Duplicate copy of original stdout back into stdout  
      if(_dup2(fdStdOut, _fileno(stdout)) != 0)  
         return   3;  
  
      // Close duplicate copy of original stdout  
      _close(fdStdOut);  
  
      if(hProcess)  
      {  
         int nOutRead;  
         while   (nExitCode == STILL_ACTIVE)  
         {  
            nOutRead = _read(fdStdOutPipe[READ_FD],   
             szBuffer, OUT_BUFF_SIZE);  
            if(nOutRead)  
            {  
               nOutRead = Filter(szBuffer, nOutRead, BEEP_CHAR);  
               fwrite(szBuffer, 1, nOutRead, stdout);  
            }  
  
            if(!GetExitCodeProcess(hProcess,(unsigned long*)&nExitCode))  
               return 4;  
         }  
      }  
   }  
   return nExitCode;  
}  
```  
  
## <a name="output"></a>輸出  
  
```  
This is speaker beep number 1...  
This is speaker beep number 2...  
This is speaker beep number 3...  
This is speaker beep number 4...  
This is speaker beep number 5...  
This is speaker beep number 6...  
This is speaker beep number 7...  
This is speaker beep number 8...  
This is speaker beep number 9...  
This is speaker beep number 10...  
```  
  
## <a name="net-framework-equivalent"></a>.NET Framework 同等  
 不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。  
  
## <a name="see-also"></a>另請參閱  
 [處理序和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [_open、_wopen](../../c-runtime-library/reference/open-wopen.md)
