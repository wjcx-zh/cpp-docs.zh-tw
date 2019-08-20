---
title: _exec、_wexec 函式
ms.date: 11/04/2016
apilocation:
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr90.dll
- msvcrt.dll
- msvcr100.dll
- msvcr110.dll
- msvcr80.dll
apitype: DLLExport
f1_keywords:
- _texecve
- texecl
- _texeclpe
- texecve
- texecv
- texeclp
- texecle
- exec
- texeclpe
- _texecvp
- _texecl
- _texecle
- wexec
- _exec
- _texeclp
- _texecvpe
- texecvpe
- _texecv
- _wexec
helpviewer_keywords:
- _texecle function
- _texecv function
- texeclpe function
- texecle function
- _texecl function
- texecv function
- _texeclp function
- _texecve function
- texecl function
- texecve function
- exec function
- texeclp function
- texecvp function
- texecvpe function
- processes, executing new
- _texecvp function
- _texeclpe function
- _wexec functions
- wexec functions
- _exec function
- _texecvpe function
ms.assetid: a261df93-206a-4fdc-b8ac-66aa7db83bc6
ms.openlocfilehash: d31192a25cce86dad6f8e1e8b0258a457d0a5436
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500142"
---
# <a name="_exec-_wexec-functions"></a>_exec、_wexec 函式

每個此系列中的函式都會載入並執行新處理序：

|||
|-|-|
|[_execl、_wexecl](../c-runtime-library/reference/execl-wexecl.md)|[_execv、_wexecv](../c-runtime-library/reference/execv-wexecv.md)|
|[_execle、_wexecle](../c-runtime-library/reference/execle-wexecle.md)|[_execve、_wexecve](../c-runtime-library/reference/execve-wexecve.md)|
|[_execlp、_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|[_execvp、_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|
|[_execlpe、_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|[_execvpe、_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|

函式名稱結尾的字母決定了變化。

|_exec 函式後置字元|說明|
|----------------------------|-----------------|
|`e`|`envp`，環境設定的指標陣列，會傳遞至新執行緒。|
|`l`|命令列引數會分別傳遞至 `_exec` 函式。 一般而言用於已預先知道新處理序的參數數目時。|
|`p`|`PATH` 環境變數，用於尋找要執行的檔案。|
|`v`|`argv`，命令列引數的指標陣列，會傳遞至 `_exec`。 一般而言用於新處理序的參數數目為變數時。|

## <a name="remarks"></a>備註

每個 `_exec` 函式都會載入並執行新處理序。 所有 `_exec` 函式會使用相同的作業系統函式 ([CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw))。 `_exec` 函式會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當且可辨識的多位元組字元序列。 `_wexec` 函式是寬字元版本的 `_exec` 函式。 `_wexec` 函式的行為和其 `_exec` 系列對應項目一樣，只不過他們不處理多位元組字元字串。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_texecl`|`_execl`|`_execl`|`_wexecl`|
|`_texecle`|`_execle`|`_execle`|`_wexecle`|
|`_texeclp`|`_execlp`|`_execlp`|`_wexeclp`|
|`_texeclpe`|`_execlpe`|`_execlpe`|`_wexeclpe`|
|`_texecv`|`_execv`|`_execv`|`_wexecv`|
|`_texecve`|`_execve`|`_execve`|`_wexecve`|
|`_texecvp`|`_execvp`|`_execvp`|`_wexecvp`|
|`_texecvpe`|`_execvpe`|`_execvpe`|`_wexecvpe`|

`cmdname` 參數會指定要執行為新處理序的檔案。 它可以指定完整路徑 (來自根目錄)、部分路徑 (來自目前的工作目錄) 或是檔案名稱。 若 `cmdname` 沒有副檔名或是沒有以句號 (.) 作為結尾，則 `_exec` 函式會搜尋命名的檔案。 若搜尋成功，函式會使用 .com 副檔名嘗試相同的基底名稱，然後使用 .exe、.bat 和 .cmd 副檔名。 若 `cmdname` 具有副檔名，則只會在搜尋中使用該副檔名。 若 `cmdname` 以句號結尾，`_exec` 會不使用副檔名搜尋 `cmdname`。 `_execlp`、`_execlpe`、`_execvp` 和 `_execvpe` 會在 `cmdname` 環境變數所指定的目錄中搜尋 `PATH` (使用相同的程序)。 若 `cmdname` 包含磁碟機代碼或任何斜線 (亦即，若為相對路徑)，則 `_exec` 只會針對指定的檔案呼叫搜尋；不會搜尋路徑。

將參數傳遞至新處理序，是透過提供一或多個指標給字元字串作為 `_exec` 呼叫中的參數。 這些字元字串會形成新處理序的參數清單。 繼承的環境設定，以及形成新處理序的參數清單的字串，兩者的合併長度不可超過 32 KB。 計數中不會包含每個字串的結束的 Null 字元 ('\0')，但會計算自動插入以區隔參數的空格字元。

> [!NOTE]
>  字串中嵌入的空格可能會導致未預期的行為；例如，傳遞字串 `_exec` 至 `"hi there"` 會導致新處理序取得兩個引數 `"hi"` 和 `"there"`。 若目的是要使新處理序開啟名為 "hi there" 的檔案，則處理序會失敗。 您可以用引號括住字串來避免此情況：`"\"hi there\""`。

> [!IMPORTANT]
>  請勿在沒有明確檢查內容的情況下將使用者輸入傳遞至 `_exec`。 `_exec` 會導致呼叫 [CreateProcess](/windows/win32/api/processthreadsapi/nf-processthreadsapi-createprocessw) (CreateProcess 函式)，所以請記得，不合格的路徑名稱可能會導致潛在的安全性漏洞。

`_exec` 函式會驗證它們的參數。 若預期的參數是 Null 指標、空字串，或是已省略，則 `_exec` 函式會叫用無效參數處理常式，如[參數驗證](../c-runtime-library/parameter-validation.md)中所述。 如果允許繼續執行，這些函式會將 `errno` 設為 `EINVAL`，並傳回 -1。 沒有執行任何新處理序。

引數指標可作為個別參數 (在 `_execl`、`_execle`、`_execlp` 和 `_execlpe` 中) 或作為指標陣列 (在 `_execv`、`_execve`、`_execvp` 和 `_execvpe` 中) 進行傳遞。 至少有一個參數 `arg0` 必須傳遞至新處理序，此參數是新處理序的 `argv`[0]。 此參數通常是 `cmdname` 的複本 (不同的值不會產生錯誤)。

一般而言，`_execl`、`_execle`、`_execlp` 和 `_execlpe` 呼叫是在已預先知道參數數目時使用。 參數 `arg0` 通常是 `cmdname` 的指標。 參數 `arg1` 到 `argn` 會指向形成新參數清單的字元字串。 Null 指標必須接在 `argn` 之後，以標示參數清單的結尾。

當新處理序的參數數目為變數時，`_execv`、`_execve`、`_execvp` 和 `_execvpe` 呼叫就很實用。 參數的指標會作為陣列 `argv` 進行傳遞。 參數 `argv`[0] 通常是 `cmdname` 的指標。 參數 `argv`[1] 到 `argv`[`n`] 會指向形成新參數清單的字元字串。 參數 `argv`[`n`+1] 必須是 **NULL** 指標，以標記參數清單的結尾。

執行 `_exec` 呼叫之後，已經開啟的檔案仍會在新處理序中保持開啟。 在 `_execl`、`_execlp`、`_execv` 和 `_execvp` 呼叫中，新處理序會繼承呼叫處理序的環境。 `_execle`、`_execlpe`、`_execve` 和 `_execvpe` 呼叫可透過 `envp` 參數傳遞環境設定的清單，來改變新處理序的環境。 `envp` 是字元指標的陣列，其中每個項目 (最後一個項目除外) 都會指向定義環境變數的以 Null 終止的字串。 此類字串通常具有此種格式：`NAME`=`value`，其中 `NAME` 是環境變數的名稱，而 `value` 是設定變數的字串值。 (請注意，`value` 沒有以雙引號括住)。`envp` 陣列的最後一個項目應為 **NULL**。 當 `envp` 本身是 **NULL** 時，新處理序會繼承呼叫處理序的環境設定。

使用其中一個 `_exec` 函式執行的程式會一律載入至記憶體中，正如同程式的 .exe 檔案標頭中的最大配置欄位是設為 0xFFFFH 的預設值。

`_exec` 呼叫不會保留開啟檔案的轉譯模式。 若新處理序必須使用繼承自呼叫處理序的檔案時，請使用 [_setmode](../c-runtime-library/reference/setmode.md) 常式以將這些檔案的轉譯模式設定為所需的模式。 您必須先明確定清除 (使用 `fflush` 或 `_flushall`) 或關閉所有資料流，再進行 `_exec` 函式呼叫。 訊號設定不會保留在由呼叫 `_exec` 常式所建立的新處理序中。 訊號設定會在新處理序中重設為預設值。

## <a name="example"></a>範例

```
// crt_args.c
// Illustrates the following variables used for accessing
// command-line arguments and environment variables:
// argc  argv  envp
// This program will be executed by crt_exec which follows.

#include <stdio.h>

int main( int argc,  // Number of strings in array argv
char *argv[],       // Array of command-line argument strings
char **envp )       // Array of environment variable strings
{
    int count;

    // Display each command-line argument.
    printf( "\nCommand-line arguments:\n" );
    for( count = 0; count < argc; count++ )
        printf( "  argv[%d]   %s\n", count, argv[count] );

    // Display each environment variable.
    printf( "\nEnvironment variables:\n" );
    while( *envp != NULL )
        printf( "  %s\n", *(envp++) );

    return;
}
```

執行下列程式以執行 Crt_args.exe：

```
// crt_exec.c
// Illustrates the different versions of exec, including
//      _execl          _execle          _execlp          _execlpe
//      _execv          _execve          _execvp          _execvpe
//
// Although CRT_EXEC.C can exec any program, you can verify how
// different versions handle arguments and environment by
// compiling and specifying the sample program CRT_ARGS.C. See
// "_spawn, _wspawn Functions" for examples of the similar spawn
// functions.

#include <stdio.h>
#include <conio.h>
#include <process.h>

char *my_env[] =     // Environment for exec?e
{
   "THIS=environment will be",
   "PASSED=to new process by",
   "the EXEC=functions",
   NULL
};

int main( int ac, char* av[] )
{
   char *args[4];
   int ch;
   if( ac != 3 ){
      fprintf( stderr, "Usage: %s <program> <number (1-8)>\n", av[0] );
      return;
   }

   // Arguments for _execv?
   args[0] = av[1];
   args[1] = "exec??";
   args[2] = "two";
   args[3] = NULL;

   switch( atoi( av[2] ) )
   {
   case 1:
      _execl( av[1], av[1], "_execl", "two", NULL );
      break;
   case 2:
      _execle( av[1], av[1], "_execle", "two", NULL, my_env );
      break;
   case 3:
      _execlp( av[1], av[1], "_execlp", "two", NULL );
      break;
   case 4:
      _execlpe( av[1], av[1], "_execlpe", "two", NULL, my_env );
      break;
   case 5:
      _execv( av[1], args );
      break;
   case 6:
      _execve( av[1], args, my_env );
      break;
   case 7:
      _execvp( av[1], args );
      break;
   case 8:
      _execvpe( av[1], args, my_env );
      break;
   default:
      break;
   }

   // This point is reached only if exec fails.
   printf( "\nProcess was not execed." );
   exit( 0 );
}
```

## <a name="requirements"></a>需求

**標頭：** process.h

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_spawn、_wspawn 函式](../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)
