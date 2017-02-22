---
title: "_spawn、_wspawn 函式 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
apilocation: 
  - "msvcr80.dll"
  - "msvcr110_clr0400.dll"
  - "msvcr110.dll"
  - "msvcrt.dll"
  - "msvcr120.dll"
  - "msvcr100.dll"
  - "msvcr90.dll"
apitype: "DLLExport"
f1_keywords: 
  - "_spawn"
  - "_tspawnlp"
  - "_tspawnlpe"
  - "_tspawnve"
  - "_tspawnvp"
  - "_tspawnvpe"
  - "_tspawnl"
  - "spawn"
  - "_tspawnv"
  - "_tspawnle"
  - "wspawn"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_tspawnve 函式"
  - "_spawn 函式"
  - "_tspawnlpe 函式"
  - "tspawnvpe 函式"
  - "處理序，建立"
  - "tspawnve 函式"
  - "_tspawnvp 函式"
  - "spawn 函式"
  - "tspawnl 函式"
  - "tspawnlp 函式"
  - "_tspawnvpe 函式"
  - "_tspawnl 函式"
  - "tspawnvp 函式"
  - "tspawnv 函式"
  - "處理序，執行新的"
  - "_tspawnv 函式"
  - "tspawnle 函式"
  - "處理序建立"
  - "_tspawnlp 函式"
  - "tspawnlpe 函式"
  - "_tspawnle 函式"
ms.assetid: bb47c703-5216-4e09-8023-8cf25bbf2cf9
caps.latest.revision: 26
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# _spawn、_wspawn 函式
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

每個 `_spawn` 函式來建立並執行處理序:  
  
|||  
|-|-|  
|[\_spawnl、\_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|[\_spawnv、\_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|  
|[\_spawnle、\_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|[\_spawnve、\_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|  
|[\_spawnlp, \_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|[\_spawnvp、\_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|  
|[\_spawnlpe、\_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|[\_spawnvpe、\_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|  
  
 函式名稱結尾的字母決定變化。  
  
 `e`  
 `envp`，也就是環境設定的指標之陣列，會傳遞至處理序。  
  
 `l`  
 命令列引數個別傳遞至 `_spawn` 函式。  事先知道這個處理序的一些參數，通常會使用後置字元。  
  
 `p`  
 `PATH` 環境變數用來尋找要執行的檔案。  
  
 `v`  
 `argv`，命令列引數的指標之陣列，會傳遞至 `_spawn`函式。  這個處理序的參數是變數時，通常就會使用這個後置字元。  
  
## 備註  
 `_spawn` 函式建立和管理處理序。  適時地自動處理多位元組字元的字串參數，根據目前使用的多位元組字碼頁來辨認多位元組字元序列。  `_wspawn` 函式是 `_spawn` 函式的寬字元版本;它們不處理多位元組字元字串。  否則， `_wspawn` 函式相同的行為與它們的 `_spawn` 對應項。  
  
### 一般文字常式對應  
  
|Tchar.h 常式|未定義 \_UNICODE and \_MBCS|\_MBCS 已定義|\_UNICODE 已定義|  
|----------------|------------------------------|----------------|-------------------|  
|`_tspawnl`|`_spawnl`|`_spawnl`|`_wspawnl`|  
|`_tspawnle`|`_spawnle`|`_spawnle`|`_wspawnle`|  
|`_tspawnlp`|`_spawnlp`|`_spawnlp`|`_wspawnlp`|  
|`_tspawnlpe`|`_spawnlpe`|`_spawnlpe`|`_wspawnlpe`|  
|`_tspawnv`|`_spawnv`|`_spawnv`|`_wspawnv`|  
|`_tspawnve`|`_spawnve`|`_spawnve`|`_wspawnve`|  
|`_tspawnvp`|`_spawnvp`|`_spawnvp`|`_wspawnvp`|  
|`_tspawnvpe`|`_spawnvpe`|`_spawnvpe`|`_wspawnvpe`|  
  
 沒有足夠的記憶體必須可供載入和執行處理序。  `mode` 引數識別呼叫程序所採取的動作在 `_spawn`之中。  `mode` 的下列值。Process.h 定義:  
  
 `_P_OVERLAY`  
 用新程序覆疊呼叫程序，破壞函式呼叫程序 \(與 `_exec` 呼叫作用相同\)。  
  
 `_P_WAIT`  
 暫停呼叫執行緒，直到處理序的完成執行 \(同步 `_spawn`\)。  
  
 `_P_NOWAIT` 或 `_P_NOWAITO`  
 繼續與新處理序 \(非同步 `_spawn`\) 同時執行呼叫程序。  
  
 `_P_DETACH`  
 繼續執行呼叫程序;處理序在背景執行，沒有對主控台或鍵盤上的存取。  呼叫 `_cwait` 物件的新處理序失敗 \(非同步 `_spawn`\)。  
  
 `cmdname` 引數指定要執行的檔案時，新的處理序，並可指定完整路徑 \(根\)，部分路徑 \(從目前的工作目錄\)，或檔案名稱。  如果 `cmdname` 沒有副檔名也以句號結束 \(\)， `_spawn` 函式會先嘗試使用 .com 副檔名、 .exe 副檔名、.bat 副檔名和最後 .cmd 副檔名。  
  
 如果 `cmdname` 有副檔名，才使用這個副檔名。  如果 `cmdname` 以句號結束， `_spawn`會呼叫搜尋 `cmdname` 不包含副檔名。  `_spawnlp`、 `_spawnlpe`、 `_spawnvp`和  `_spawnvpe` 會在 `PATH` 環境變數指定的目錄中函式搜尋 `cmdname` \(使用相同的程序\)。  
  
 如果 `cmdname` 包含磁碟機指定名稱或任何斜線 \(也就是說，如果是相對路徑\)， `_spawn` 會呼叫只搜尋指定的檔案；路徑不會搜尋。  
  
 在過去，這些函式調整 `errno` 為零在成功;目前的行為是保留給 `errno` 未觸發引動過程都已指定，根據 C 標準。  如果您需要模擬舊版行為，調整 `errno` 為零在呼叫這些函式之前。  
  
> [!NOTE]
>  若要確保適當的覆疊初始化和終止，不要使用 `setjmp` 或 `longjmp` 函式進入或離開覆疊常式。  
  
## 產生之處理序的引數。  
 若要將引數傳遞至處理序，請將一個或多個指標字串，在 `_spawn` 呼叫中的引數。  這些字串會產生之處理序的引數清單。  建立新的處理序的字串的長度引數清單不能超過 1024 個位元組。  每個字串的結束 null 字元 \(「\\ 0 」\) 不包含計數，但空白字元 \(自動插入以分隔參數\) 會列入。  
  
> [!NOTE]
>  在字串中的空間可能會造成未預期的行為：例如，傳遞 `_spawn` 字串 `"hi there"` 將會產生取得兩個引數：`"hi"` 和 `"there"`的新處理序。  如果目的是有開啟名為「hi there」的檔案之新處理序，處理序就會失敗。  您可以將字串放在引號內以避免這個問題：`"\"hi there\""`。  
  
> [!IMPORTANT]
>  不要在不明確地檢查其內容的情況下，將使用者輸入傳遞到 `_spawn` 。  `_spawn` 會導致呼叫 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425) ，因此請記住不完整的路徑名稱可能會造成潛在的安全性漏洞。  
  
 您可以將引數傳遞指標當做個別的引數 \( `_spawnl`、 `_spawnle`、 `_spawnlp`和 `_spawnlpe`\) 或做為陣列指標 \( `_spawnv`、 `_spawnve`、 `_spawnvp`和 `_spawnvpe`\)。  您必須將引數、至少 `arg0` 或 `argv`\[0\]，以產生的處理序。  依照慣例，您可以輸入在命令列中的引數為程式的名稱。  不一樣的值不會產生錯誤。  
  
 `_spawnl`、 `_spawnle`、 `_spawnlp`和 `_spawnlpe` 呼叫，在引數數目事先知道處理，通常會使用。  `arg0` 引數通常是指向 `cmdname` 的指標。  引數 `arg1` 至 `argn` 是指向形成新的引數清單的字元字串。  `argn`之後必須有一個 `NULL` 指標，以標記引數清單的結尾。  
  
 當有引數的變數數字至處理序時， `_spawnv`、 `_spawnve`、 `_spawnvp`和 `_spawnvpe` 呼叫很有用。  引數的指標會作為陣列傳遞，為 `argv`。引數 `argv`\[0\] 通常是指向路由模式中的路徑或受保護模式中的程序名稱之指標，而 `argv`\[1\] 至 `argv`\[`n`\] 是指向形成新的引數清單的字串。  引數 `argv`\[`n` \+1\] 必須是 `NULL` 指標，以標記引數清單的結尾。  
  
## 產生之處理序的環境  
 當 `_spawn` 的呼叫在新處理序保持開啟時開啟的檔案。  在 `_spawnl`、 `_spawnlp`、 `_spawnv` 和 `_spawnvp` 呼叫中，新處理序會繼承呼叫處理序的環境。  您可以使用 `_spawnle`、 `_spawnlpe`、 `_spawnve`和 `_spawnvpe` 呼叫傳遞環境設定清單修改新處理序的環境 `envp` 引數。  引數`envp` 為字元陣列指標，其中每個項目 \(除了最後一個項目\) 指向定義環境變數的 NULL 結尾字串。  這種資料通常有 `NAME` 為環境變數名稱的格式為 `NAME`\=`value` ，且 `value` 為該變數設定的字串值。\(請注意 `value` 以沒有被雙引號括住\)。`envp` 陣列的最後一個項目應為 `NULL`。  當 `envp` 本身為 `NULL` 時，衍生處理序會繼承父處理序的環境設定。  
  
 `_spawn` 函式可以將更新程序傳遞至開啟檔案的所有資訊，包括版本模式。  這項資訊在執行路由模式將 `C_FILE_INFO` 項目加入至環境中。  啟始程式碼通常會處理這個輸入然後刪除從環境。  不過，如果 `_spawn` 函式，產生非 C\# 程序，這個項目會在環境維持。  因為環境資訊在執行路由模式，將二進位形式列印環境在這個項目的定義字串顯示對應的。  它不應該對一般作業的其他作用。  以受保護模式下，環境資訊會以文字形式也不包含對應字元。  
  
 您必須明確地清除 \(使用 `fflush` 或 `_flushall`\) 或 `_spawn` 函式呼叫之前關閉資料流。  
  
 呼叫所建立的新處理序對 `_spawn` 常式不保留信號設定。  相反地，對預設產生的處理重設信號設定。  
  
## 重新導向輸出  
 如果您呼叫從 DLL 或 GUI 應用程式的 `_spawn` 以及要將輸出重新導向至管道，您有兩個選項:  
  
-   使用 Win32 API 建立管道，然後呼叫 [AllocConsole](http://msdn.microsoft.com/library/windows/desktop/ms681944)，設定在開始的結構和呼叫 [CreateProcess](http://msdn.microsoft.com/library/windows/desktop/ms682425)的控制代碼值。  
  
-   呼叫會建立管道的 [\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md) 並叫用應用程式使用 **cmd.exe \/c** \(或 **command.exe \/c**\)。  
  
## 範例  
  
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
  
  **子處理序輸出**  
**從繁衍\!**   
## 請參閱  
 [流程控制和環境控制](../c-runtime-library/process-and-environment-control.md)   
 [abort](../c-runtime-library/reference/abort.md)   
 [atexit](../c-runtime-library/reference/atexit.md)   
 [\_exec、\_wexec 函式](../c-runtime-library/exec-wexec-functions.md)   
 [exit, \_Exit, \_exit](../c-runtime-library/reference/exit-exit-exit.md)   
 [\_flushall](../c-runtime-library/reference/flushall.md)   
 [\_getmbcp](../c-runtime-library/reference/getmbcp.md)   
 [\_onexit，\_onexit\_m](../c-runtime-library/reference/onexit-onexit-m.md)   
 [\_setmbcp](../c-runtime-library/reference/setmbcp.md)   
 [system、\_wsystem](../c-runtime-library/reference/system-wsystem.md)