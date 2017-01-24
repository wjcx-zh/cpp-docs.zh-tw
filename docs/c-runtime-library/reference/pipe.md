---
title: "_pipe | Microsoft Docs"
ms.custom: ""
ms.date: "12/16/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apiname: 
  - "_pipe"
apilocation: 
  - "msvcrt.dll"
  - "msvcr80.dll"
  - "msvcr90.dll"
  - "msvcr100.dll"
  - "msvcr100_clr0400.dll"
  - "msvcr110.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr120.dll"
  - "msvcr120_clr0400.dll"
  - "ucrtbase.dll"
  - "api-ms-win-crt-stdio-l1-1-0.dll"
apitype: "DLLExport"
f1_keywords: 
  - "pipe"
  - "_pipe"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "_pipe 函式"
  - "pipe 函式"
  - "管道"
  - "管道, 建立"
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# _pipe
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

建立用於讀取和寫入的管道。  
  
> [!IMPORTANT]
>  這個應用程式開發介面不能用於 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)] 中執行的應用程式。  如需詳細資訊，請參閱 [\/ZW 不支援 CRT 函式](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx)。  
  
## 語法  
  
```  
  
      int _pipe(  
int *pfds,  
unsigned int psize,  
int textmode   
);  
```  
  
#### 參數  
 `pfds`\[2\]  
 用於保留讀取和寫入檔案描述項的陣列。  
  
 `psize`  
 記憶體保存的量。  
  
 `textmode`  
 檔案模式。  
  
## 傳回值  
 如果成功則傳回 0。  傳回 –1 表示錯誤。  發生錯誤時， `errno` 會設為下列其中一個值：  
  
-   `EMFILE`，表示沒有其他檔案描述項是可用的。  
  
-   `ENFILE`，表示系統檔案表溢位。  
  
-   `EINVAL`，表示 `pfds` 陣列為 null 指標或傳遞的 `textmode` 之值為無效。  
  
 如需有關這些傳回碼和其他傳回碼的詳細資訊，請參閱 [errno、\_doserrno、\_sys\_errlist 和 \_sys\_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。  
  
## 備註  
 `_pipe` 函式會建立 *管道*，是一條程式用來傳遞資訊至其他程式的人工 I\/O 通道。  管道類似檔案，因為它擁有檔案指標、檔案描述項或兩者皆有，且它可使用標準程式庫輸入和輸出函式被讀取或寫入。  不過，管道不代表特定檔案或裝置。  相反地，它表示與程式的記憶體獨立且完全由作業系統控制的記憶體之暫時儲存區。  
  
 `_pipe` 與 `_open` 類似，但它開啟管道來讀取和寫入並傳回兩個檔案描述項而不是一個。  程式可以使用管道的兩方或關閉其中不需要的一方。  例如，當命令處理器在 Windows 執行命令 \(例如 `PROGRAM1 | PROGRAM2`\) 時，建立管道。  
  
 `PROGRAM1` 的標準輸出描述項連結至管道的寫入描述項。  `PROGRAM2` 的標準輸入描述項連結至管道的讀取描述項。  如此便不需要建立暫存檔案給其他程式傳遞資訊。  
  
 `_pipe` 函式會傳回兩個檔案描述項於 `pfds` 引數的管道。  這個項目 `pfds`\[0\] 包含讀取描述項，而項目 `pfds`\[1\] 包含寫入描述項。  管道檔描述項與其他檔案描述項以相同的方式使用。\(低階輸入和輸出函式 `_read` 和 `_write` 可以讀取和寫入管道\)。若要偵測關閉管道情況，請檢查傳回 0 \(作為讀取位元組數 \)的 `_read` 要求。  
  
 `psize` 引數會指定位元組記憶體量，用來為管道保留。  `textmode` 引數為管道指定轉譯模式。  資訊清單常數 `_O_TEXT` 指定為文字轉譯，而常數 `_O_BINARY` 指定為二進位轉譯。\(文字和二進位模式的說明請參閱 [fopen、\_wfopen](../../c-runtime-library/reference/fopen-wfopen.md) \)。如果 `textmode` 引數為 0， `_pipe` 使用由預設模式變數 [\_fmode](../../c-runtime-library/fmode.md) 所指定的預設轉譯模式。  
  
 在多執行緒的程式，鎖定不會執行。  傳回的檔案描述項是新開啟的，且在 `_pipe` 呼叫完成之前不能由任何執行緒參考。  
  
 若要使用 `_pipe` 函式作父處理序與子處理序之間的溝通，每個處理序只能有一個描述項在管道上開啟。  描述項必須是相對的：如果父代已有一個讀取描述項開啟，則子系必須有一個寫入描述項開啟。  最簡單的方式是 `OR` \(  `|`\) 具有 `textmode` 的 `_O_NOINHERIT` 旗標。  然後，使用 `_dup` 或 `_dup2` 建立您想要傳遞給子系的管道描述項之可繼承的複本。  關閉原始的描述項，然後產生子處理序。  在從傳回繁衍呼叫時，關閉在父處理序的複本描述項。  如需詳細資訊，請參閱本文稍後的範例 2 。  
  
 在 Windows 作業系統，當管道所有的描述項關閉時，管道會終結。\(如果所有管道的讀取描述項已被關閉，則寫入管道會產生錯誤\)。所有管道的讀取和寫入作業，都會等待直到有完成 I\/O 要求之足夠的資料或足夠的緩衝區空間。  
  
## 需求  
  
|常式|必要的標頭|選擇性標頭|  
|--------|-----------|-----------|  
|`_pipe`|\<io.h\>|\<fcntl.h\>,1 \<errno.h\>2|  
  
 1 為 `_O_BINARY` 和 `_O_TEXT` 定義。  
  
 2 `errno` 定義  
  
 如需詳細的相容性資訊，請參閱[相容性](../../c-runtime-library/compatibility.md)。  
  
## 程式庫  
 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)的所有版本。  
  
## 範例 1  
  
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
  
## 範例輸出  
  
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
  
## 範例 2  
 這是一個基本的篩選應用程式。  它會在建立一個將產生的應用程式之 stdout 導向篩選器的管道之後，產生應用程式 crt\_pipe\_beeper。  篩選器移除 ASCII 7 \(嗶聲\) 字元。  
  
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
  
## Output  
  
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
  
## .NET Framework 對等用法  
 不適用。若要呼叫標準 C 函式，請使用 `PInvoke`。如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。  
  
## 請參閱  
 [流程控制和環境控制](../../c-runtime-library/process-and-environment-control.md)   
 [\_open、\_wopen](../../c-runtime-library/reference/open-wopen.md)