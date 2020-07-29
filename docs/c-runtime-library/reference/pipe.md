---
title: _pipe
ms.date: 4/2/2020
api_name:
- _pipe
- _o__pipe
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
- api-ms-win-crt-stdio-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- pipe
- _pipe
helpviewer_keywords:
- pipes, creating
- _pipe function
- pipes
- pipe function
ms.assetid: 8d3e9800-4041-44b5-9e93-2df0b0354a75
ms.openlocfilehash: 692a891549e0c84d6297b108918d9d7c58495ef7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87234038"
---
# <a name="_pipe"></a>_pipe

建立用於讀取和寫入的管道。

> [!IMPORTANT]
> 這個 API 不能用於在 Windows 執行階段中執行的應用程式。 如需詳細資訊，請參閱 [CRT functions not supported in Universal Windows Platform apps](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md) (通用 Windows 平台應用程式中不支援的 CRT 函式)。

## <a name="syntax"></a>語法

```C
int _pipe(
   int *pfds,
   unsigned int psize,
   int textmode
);
```

### <a name="parameters"></a>參數

*pfds*<br/>
包含讀取和寫入檔案描述元之二陣列的指標 **`int`** 。

*psize*<br/>
要保留的記憶體數量。

*textmode*<br/>
檔案模式。

## <a name="return-value"></a>傳回值

若成功，即傳回 0。 傳回-1 表示發生錯誤。 發生錯誤時， **errno**會設定為下列其中一個值：

- **EMFILE**，表示沒有更多可用的檔案描述項。

- **ENFILE**，表示系統檔案資料表溢位。

- **EINVAL**，表示陣列*pfds*為 null 指標，或傳入*textmode*的無效值。

如需這些傳回碼和其他傳回碼的詳細資訊，請參閱[errno、_doserrno、_sys_errlist 和 _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md)。

## <a name="remarks"></a>備註

**_Pipe**函式會建立一個*管道*，這是一個人工 i/o 通道，程式會使用它將資訊傳遞給其他程式。 管道類似於檔案，因為它具有檔案指標及 (或) 檔案描述項，而且可以透過使用標準程式庫輸入和輸出函式從中讀取或寫入至其中。 不過，管道並不代表特定檔案或裝置。 相反地，它代表與程式本身記憶體無關，而且完全由作業系統控制之記憶體中的暫存位置。

**_pipe**類似 **_open**但會開啟用來讀取和寫入的管道，並傳回兩個檔案描述項，而不是一個。 程式可以在管道兩端使用，或關閉不需要的一端。 例如，Windows 中的命令處理器會在執行命令時建立管道，例如**PROGRAM1**  |  **program2.c**。

**PROGRAM1**的標準輸出描述元會附加至管道的寫入描述項。 **Program2.c**的標準輸入描述元會附加至管道的讀取描述項。 如此一來，就不需要建立暫存檔來將資訊傳遞至其他程式。

**_Pipe**函式會將兩個檔案描述項傳回到*pfds*引數中的管道。 元素*pfds*[0] 包含讀取描述元，而*pfds*[1] 元素則包含寫入描述元。 管道檔案描述項的使用方式與其他檔案描述項相同 （低層級的輸入和輸出函數 **_read** ， **_write**可以讀取和寫入管道）。若要偵測管道結束條件，請檢查是否有傳回0的 **_read**要求，做為讀取的位元組數目。

*Psize*引數會指定要為管道保留的記憶體數量（以位元組為單位）。 *Textmode*引數會指定管道的轉譯模式。 資訊清單常數 **_O_TEXT**指定文字轉譯，而常數 **_O_BINARY**指定二進位轉譯。 （如需文字和二進位模式的說明，請參閱[fopen、_wfopen](fopen-wfopen.md) ）。如果*textmode*引數為0， **_pipe**會使用預設模式變數所指定的預設轉譯模式[_fmode](../../c-runtime-library/fmode.md)。

在多執行緒程式中，不會執行任何鎖定。 傳回的檔案描述項會新開啟，而且在 **_pipe**呼叫完成之前，任何執行緒都不應該參考它們。

若要使用 **_pipe**函式在父進程和子進程之間進行通訊，每個處理常式都必須在管道上開啟一個描述項。 這兩個描述項必須相反：如果父系開啟讀取描述項，則子系就必須開啟寫入描述項。 若要這麼做，最簡單的方式是 **|** 使用*textmode*的位 or （） **_O_NOINHERIT**旗標。 然後，使用 **_dup**或 **_dup2** ，建立您要傳遞至子系之管道描述元的可繼承複本。 關閉原始描述項，然後繁衍子處理序。 從繁衍呼叫傳回時，請關閉父處理序中重複的描述項。 如需詳細資訊，請參閱本文稍後的範例 2。

在 Windows 作業系統中，當管道的所有描述項都已關閉時，就會終結管道 （如果管道上的所有讀取描述項都已關閉，則寫入管線會導致錯誤）。管道上的所有讀取和寫入作業都會等到有足夠的資料或足夠的緩衝區空間來完成 i/o 要求為止。

根據預設，此函式的全域狀態範圍設定為應用程式。 若要變更此項，請參閱[CRT 中的全域狀態](../global-state.md)。

## <a name="requirements"></a>需求

|常式傳回的值|必要的標頭|選擇性標頭|
|-------------|---------------------|---------------------|
|**_pipe**|\<io.h>|\<fcntl.h>，1 \<errno.h> 2|

1適用于 **_O_BINARY**和 **_O_TEXT**定義。

2 **errno**定義。

如需詳細的相容性資訊，請參閱 [Compatibility](../../c-runtime-library/compatibility.md)。

## <a name="libraries"></a>程式庫

所有版本的 [C 執行階段程式庫](../../c-runtime-library/crt-library-features.md)。

## <a name="example-1"></a>範例 1

```C
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

```Output
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

```C
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

```C
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

```Output
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

## <a name="see-also"></a>另請參閱

[進程和環境控制](../../c-runtime-library/process-and-environment-control.md)<br/>
[_open、_wopen](open-wopen.md)<br/>
