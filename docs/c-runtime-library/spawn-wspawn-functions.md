---
title: _spawn、_wspawn 函式
ms.date: 11/04/2016
apilocation:
- msvcr80.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr100.dll
- msvcr90.dll
apitype: DLLExport
f1_keywords:
- _spawn
- _tspawnlp
- _tspawnlpe
- _tspawnve
- _tspawnvp
- _tspawnvpe
- _tspawnl
- spawn
- _tspawnv
- _tspawnle
- wspawn
helpviewer_keywords:
- _tspawnve function
- _spawn functions
- _tspawnlpe function
- tspawnvpe function
- processes, creating
- tspawnve function
- _tspawnvp function
- spawn functions
- tspawnl function
- tspawnlp function
- _tspawnvpe function
- _tspawnl function
- tspawnvp function
- tspawnv function
- processes, executing new
- _tspawnv function
- tspawnle function
- process creation
- _tspawnlp function
- tspawnlpe function
- _tspawnle function
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
ms.openlocfilehash: 044aaee376be02d0d3734ea8982a8c4db47f7d39
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57748043"
---
# <a name="spawn-wspawn-functions"></a>_spawn、_wspawn 函式

所有 `_spawn` 函式都會建立並執行新的處理序：

|||
|-|-|
|[_spawnl、_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[_spawnv、_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|
|[_spawnle、_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[_spawnve、_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|
|[_spawnlp、_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[_spawnvp、_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|
|[_spawnlpe、_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[_spawnvpe、_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|

函式名稱結尾的字母決定了變化。

|字母|變異|
|-|-|
| `e`  | `envp`，環境設定的指標陣列，會傳遞至新處理序。  |
| `l`  | 命令列引數會分別傳遞至 `_spawn` 函式。 當預先知道新處理序的參數數目時，通常會使用此尾碼。  |
| `p`  | `PATH` 環境變數，用於尋找要執行的檔案。  |
| `v`  | `argv`，命令列引數的指標陣列，會傳遞至 `_spawn` 函式。 當預先知道新處理序的參數數目時，通常會使用此尾碼。  |

## <a name="remarks"></a>備註

所有的 `_spawn` 函式都會建立並執行新的處理序。 它們會根據目前使用中的多位元組字碼頁，自動將多位元組字元字串引數處理為適當且可辨識的多位元組字元序列。 `_wspawn` 函式是寬字元版的 `_spawn` 函式，它們不會處理多位元組字元字串。 否則，`_wspawn` 函式的行為會和其 `_spawn` 對應項目相同。

### <a name="generic-text-routine-mappings"></a>一般文字常式對應

|Tchar.h 常式|未定義 _UNICODE 和 _MBCS|_MBCS 已定義|_UNICODE 已定義|
|---------------------|--------------------------------------|--------------------|-----------------------|
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|

必須有足夠的記憶體才能載入和執行新的處理序。 `mode` 引數會決定呼叫處理序在 `_spawn` 之前及期間所採取的動作。 `mode` 的下列值是在 Process.h 中定義︰

|||
|-|-|
| `_P_OVERLAY`  | 重疊呼叫處理序與新的處理序，會終結呼叫處理序 (與 `_exec` 呼叫的效果相同)。  |
| `_P_WAIT`  | 暫停呼叫執行緒直到新的處理序執行完成 (同步的 `_spawn`)。  |
| `_P_NOWAIT` 或 `_P_NOWAITO`  | 同時繼續執行呼叫處理序與新的處理序 (非同步的 `_spawn`)。  |
| `_P_DETACH`  | 繼續執行呼叫處理序，新處理序在背景執行，但無法存取主控台或鍵盤。 針對新的處理序呼叫 `_cwait` 失敗 (非同步的 `_spawn`)。  |

`cmdname` 引數指定當做新處理序執行的檔案，而且可以指定完整路徑 (來自根目錄)、部分路徑 (來自目前的工作目錄) 或僅只檔案名稱。 如果 `cmdname` 沒有副檔名或結尾不是句號 (.)，`_spawn` 函式就會先嘗試 .com 副檔名，再嘗試 .exe 副檔名、.bat 副檔名，最後是 .cmd 副檔名。

若 `cmdname` 有副檔名，就只使用該副檔名。 若 `cmdname` 以句號結尾，`_spawn` 呼叫會不使用副檔名搜尋 `cmdname`。 `_spawnlp`、`_spawnlpe`、`_spawnvp` 和 `_spawnvpe` 函式會在 `PATH` 環境變數指定的目錄中搜尋 `cmdname` (使用相同的程序)。

若 `cmdname` 包含磁碟機代碼或任何斜線 (亦即，若為相對路徑)，則 `_spawn` 呼叫只會搜尋指定的檔案，不會搜尋任何路徑。

以前，這些函式有些會在成功時將 `errno` 設成零，目前的行為則是在成功時，如 C 標準所指定的維持 `errno` 原封不動。 如果您需要模擬舊版的行為，只要在呼叫這些函式前將 `errno` 設為零即可。

> [!NOTE]
>  若要確保正確的重疊初始化及終止，請勿使用 `setjmp` 或 `longjmp` 函式進入或離開重疊常式。

## <a name="arguments-for-the-spawned-process"></a>繁衍處理序的引數

若要將引數傳遞給新的處理序，請提供一或多個字元字串的指標當做 `_spawn` 呼叫中的引數。 這些字元字串會形成繁衍處理序的引數清單。 形成新處理序引數清單的字串合併長度不得超過 1024 個位元組。 計數中不會包含每個字串的終止 Null 字元 ('\0')，但會包含自動插入以區隔引數的空格字元。

> [!NOTE]
>  字串中嵌入的空格可能會導致未預期的行為；例如，傳遞字串 `_spawn` 至 `"hi there"` 會導致新處理序取得兩個引數 `"hi"` 和 `"there"`。 若目的是要使新處理序開啟名為 "hi there" 的檔案，則處理序會失敗。 您可以用引號括住字串來避免此情況：`"\"hi there\""`。

> [!IMPORTANT]
>  請勿在沒有明確檢查內容的情況下將使用者輸入傳遞至 `_spawn`。 `_spawn` 會導致呼叫 [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) (CreateProcess 函式)，所以請記得，不合格的路徑名稱可能會導致潛在的安全性漏洞。

您可以將引數指標當做個別的參數 (在 `_spawnl`、`_spawnle`、`_spawnlp` 和 `_spawnlpe` 中) 或指標陣列 (在 `_spawnv`、`_spawnve`、`_spawnvp` 和 `_spawnvpe` 中) 傳遞。 您必須至少將一個引數，`arg0` 或 `argv`[0]，傳遞至繁衍的處理序。 依照慣例，此引數是您會在命令列上輸入的程式名稱。 不同的值不會產生錯誤。

`_spawnl`、`_spawnle`、`_spawnlp` 和 `_spawnlpe` 呼叫通常是在預知引數數目時使用。 `arg0` 引數通常是 `cmdname`的指標。 `arg1` 到 `argn` 的引數是形成新引數清單之字元字串的指標。 `argn` 之後必須有一個 **NULL** 指標，以標記引數清單的結尾。

當新處理序的引數數目可變時，`_spawnv`、`_spawnve`、`_spawnvp` 和 `_spawnvpe` 呼叫就很實用。 引數的指標會當做陣列 `argv` 傳遞。 引數 `argv`[0] 通常是真實模式中的路徑或受保護模式中程序名稱的指標，而 `argv`[1] 至 `argv`[`n`] 是形成新引數清單之字元字串的指標。 引數 `argv`[`n` +1] 必須是 **NULL** 指標，以標記引數清單的結尾。

## <a name="environment-of-the-spawned-process"></a>繁衍處理序的環境

執行 `_spawn` 呼叫之後，已經開啟的檔案仍會在新處理序中保持開啟。 在 `_spawnl`、`_spawnlp`、`_spawnv` 和 `_spawnvp` 呼叫中，新處理序會繼承呼叫處理序的環境。 您可以使用 `_spawnle`、`_spawnlpe`、`_spawnve` 和 `_spawnvpe` 呼叫透過 `envp` 引數傳遞環境設定的清單，來改變新處理序的環境。 引數 `envp` 是字元指標的陣列，其每個項目 (最後一個項目除外) 都會指向定義環境變數的以 Null 終止的字串。 此類字串通常具有此種格式：`NAME`=`value`，其中 `NAME` 是環境變數的名稱，而 `value` 是設定變數的字串值。 (請注意，`value` 沒有以雙引號括住)。`envp` 陣列的最後一個項目應為 **NULL**。 當 `envp` 本身是 **NULL** 時，繁衍的處理序會繼承父代處理序的環境設定。

`_spawn` 函式可以將開啟的檔案的所有資訊，包括轉譯模式在內，傳遞至新的處理序。 這項資訊會透過環境中的 `C_FILE_INFO` 項目以真實模式傳遞。 啟始程式碼通常會處理此項目，再從環境中刪除它。 不過，如果 `_spawn` 函式產生非 C 程序，此項目會保留在環境中。 列印環境會在此項目的定義字串中顯示圖形字元，因為環境資訊以真實模式的二進位格式傳遞。 它對正常作業應該沒有任何其他影響。 在受保護的模式中，環境資訊會以文字格式傳遞，因此不包含任何圖形字元。

您必須先明確清除 (使用 `fflush` 或 `_flushall`) 或關閉所有資料流，再呼叫 `_spawn` 函式。

由 `_spawn` 常式呼叫建立的新處理序中不會保留訊號設定。 繁衍處理序會改將訊號設定重設為預設值。

## <a name="redirecting-output"></a>正在重新導向輸出

如果從 DLL 或 GUI 應用程式呼叫 `_spawn`，而且想要將輸出重新導向至管道，您有兩個選項︰

- 使用 Win32 API 建立管道，然後呼叫[AllocConsole](/windows/console/allocconsole) (AllocConsole 函式)，在啟動結構中設定控制代碼值，再呼叫 [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) (CreateProcess 函式)。

- 呼叫會建立管道的 [_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)，並叫用使用 **cmd.exe /c** (或 **command.exe /c**) 的應用程式。

## <a name="example"></a>範例

```
// crt_spawn.c
// This program accepts a number in the range
// 1-8 from the command line. Based on the number it receives,
// it executes one of the eight different procedures that
// spawn the process named child. For some of these procedures,
// the CHILD.EXE file must be in the same directory; for
// others, it only has to be in the same path.
//

#include <stdio.h>
#include <process.h>

char *my_env[] =
{
   "THIS=environment will be",
   "PASSED=to child.exe by the",
   "_SPAWNLE=and",
   "_SPAWNLPE=and",
   "_SPAWNVE=and",
   "_SPAWNVPE=functions",
   NULL
};

int main( int argc, char *argv[] )
{
   char *args[4];

   // Set up parameters to be sent:
   args[0] = "child";
   args[1] = "spawn??";
   args[2] = "two";
   args[3] = NULL;

   if (argc <= 2)
   {
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }

   switch (argv[1][0])   // Based on first letter of argument
   {
   case '1':
      _spawnl( _P_WAIT, argv[2], argv[2], "_spawnl", "two", NULL );
      break;
   case '2':
      _spawnle( _P_WAIT, argv[2], argv[2], "_spawnle", "two",
               NULL, my_env );
      break;
   case '3':
      _spawnlp( _P_WAIT, argv[2], argv[2], "_spawnlp", "two", NULL );
      break;
   case '4':
      _spawnlpe( _P_WAIT, argv[2], argv[2], "_spawnlpe", "two",
                NULL, my_env );
      break;
   case '5':
      _spawnv( _P_OVERLAY, argv[2], args );
      break;
   case '6':
      _spawnve( _P_OVERLAY, argv[2], args, my_env );
      break;
   case '7':
      _spawnvp( _P_OVERLAY, argv[2], args );
      break;
   case '8':
      _spawnvpe( _P_OVERLAY, argv[2], args, my_env );
      break;
   default:
      printf( "SYNTAX: SPAWN <1-8> <childprogram>\n" );
      exit( 1 );
   }
   printf( "from SPAWN!\n" );
}
```

```Output
child process output
from SPAWN!
```

## <a name="see-also"></a>另請參閱

[流程控制和環境控制](../c-runtime-library/process-and-environment-control.md)<br/>
[abort](../c-runtime-library/reference/abort.md)<br/>
[atexit](../c-runtime-library/reference/atexit.md)<br/>
[_exec、_wexec 函式](../c-runtime-library/exec-wexec-functions.md)<br/>
[exit、_Exit、_exit](../c-runtime-library/reference/exit-exit-exit.md)<br/>
[_flushall](../c-runtime-library/reference/flushall.md)<br/>
[_getmbcp](../c-runtime-library/reference/getmbcp.md)<br/>
[_onexit、_onexit_m](../c-runtime-library/reference/onexit-onexit-m.md)<br/>
[_setmbcp](../c-runtime-library/reference/setmbcp.md)<br/>
[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)
