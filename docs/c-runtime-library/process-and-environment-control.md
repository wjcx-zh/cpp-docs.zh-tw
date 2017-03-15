---
title: "處理序控制和環境控制 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- c.programs
dev_langs:
- C++
helpviewer_keywords:
- processes, stopping
- processes, administrative tasks
- parent process
- processes, starting
- environment control routines
- process control routines
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
caps.latest.revision: 9
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
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: d5198dcef7d24d2755c21b90802b19e809c5b8da
ms.lasthandoff: 02/24/2017

---
# <a name="process-and-environment-control"></a>處理序控制和環境控制
使用處理序控制常式可從程式內啟動、停止及管理處理序。 使用環境控制常式可取得和變更作業系統環境的相關資訊。  
  
### <a name="process-and-environment-control-functions"></a>處理序控制和環境控制函式  
  
|常式|用法|.NET Framework 同等|  
|-------------|---------|-------------------------------|  
|[abort](../c-runtime-library/reference/abort.md)|中止處理序，而不會清除緩衝區或呼叫 `atexit` 和 `_onexit` 註冊的函式|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|測試邏輯錯誤|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[_ASSERT、_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集|類似於 `assert`，但僅適用於偵錯版本的執行階段程式庫|[System::Diagnostics::Debug::Assert](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[atexit](../c-runtime-library/reference/atexit.md)|排程常式在程式終止時執行|[System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|在 Windows 作業系統處理序上建立新的執行緒|[System::Threading::Thread::Start](https://msdn.microsoft.com/en-us/library/system.threading.thread.start.aspx)|  
|[_cexit](../c-runtime-library/reference/cexit-c-exit.md)|執行 `exit` 終止程序 (例如清除緩衝區)，然後將控制權交還給呼叫程式而不終止處理序|[System::Diagnostics::Process::CloseMainWindow](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[_c_exit](../c-runtime-library/reference/cexit-c-exit.md)|執行 `_exit` 終止程序，然後將控制權交還給呼叫程式而不終止處理序|[System::Diagnostics::Process::CloseMainWindow](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[_cwait](../c-runtime-library/reference/cwait.md)|等到其他處理序終止為止|[System::Diagnostics::Process::WaitForExit](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.waitforexit.aspx)|  
|[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|終止 Windows 作業系統執行緒|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_execl、_wexecl](../c-runtime-library/reference/execl-wexecl.md)|使用引數清單執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execle、_wexecle](../c-runtime-library/reference/execle-wexecle.md)|使用引數清單和指定的環境執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execlp、_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|使用 `PATH` 變數和引數清單執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execlpe、_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|使用 `PATH` 變數、指定的環境和引數清單執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execv、_wexecv](../c-runtime-library/reference/execv-wexecv.md)|使用引數陣列執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execve、_wexecve](../c-runtime-library/reference/execve-wexecve.md)|使用引數陣列和指定的環境執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execvp、_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|使用 `PATH` 變數和引數陣列執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_execvpe、_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|使用 `PATH` 變數、指定的環境和引數陣列執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|呼叫 `atexit` 和 `_onexit` 註冊的函式、清除所有緩衝區、關閉所有開啟的檔案，並且終止處理序|[System::Diagnostics::Process::Kill](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[_exit](../c-runtime-library/reference/exit-exit-exit.md)|立即終止處理序而不呼叫 `atexit` 或 `_onexit` 或清除緩衝區|[System::Diagnostics::Process::Kill](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[getenv、_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)、[getenv_s、_wgetenv_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|取得環境變數的值|[System::Environment::GetEnvironmentVariable](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)|  
|[_getpid](../c-runtime-library/reference/getpid.md)|取得處理序 ID 編號|[System::Diagnostics::Process::Id](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|  
|[longjmp](../c-runtime-library/reference/longjmp.md)|還原儲存的堆疊環境；使用它來執行非區域的 `goto`|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|排程常式在程式終止時執行；為了與 Microsoft C/C++ 版本 7.0 或更早版本的相容性而使用|[System::Diagnostics::Process::Exited](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[_pclose](../c-runtime-library/reference/pclose.md)|等候新的命令處理程式，然後關閉相關管道上的資料流|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[perror、_wperror](../c-runtime-library/reference/perror-wperror.md)|列印錯誤訊息|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_pipe](../c-runtime-library/reference/pipe.md)|建立用於讀取和寫入的管道|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_popen、_wpopen](../c-runtime-library/reference/popen-wpopen.md)|建立管道並執行命令|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_putenv、_wputenv](../c-runtime-library/reference/putenv-wputenv.md)、[_putenv_s、_wputenv_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|新增或變更環境變數的值|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[raise](../c-runtime-library/reference/raise.md)|將訊號傳送至呼叫處理序|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[setjmp](../c-runtime-library/reference/setjmp.md)|儲存堆疊環境；用來執行非區域的 `goto`|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[signal](../c-runtime-library/reference/signal.md)|處理插斷訊號|不適用。 若要呼叫標準 C 函式，請使用 `PInvoke`。 如需詳細資訊，請參閱[平台叫用範例](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f)。|  
|[_spawnl、_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|使用指定的引數清單建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnle、_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|使用指定的引數清單和環境建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnlp、_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|使用 `PATH` 變數和指定的引數清單建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnlpe、_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|使用 `PATH` 變數、指定的環境和引數清單建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnv、_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|使用指定的引數陣列建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnve、_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|使用指定的環境和引數陣列建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnvp、_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|使用 `PATH` 變數和指定的引數陣列建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[_spawnvpe、_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|使用 `PATH` 變數、指定的環境和引數陣列建立並執行新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)、[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[system、_wsystem](../c-runtime-library/reference/system-wsystem.md)|執行作業系統命令|[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)、[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)|  
  
 在 Windows 作業系統中，被繁衍的處理序相當於繁衍的處理序。 任何處理序都可以使用 `_cwait` 等候處理序識別碼已知的任何其他處理序。  
  
 `_exec` 和 `_spawn` 系列之間的差異是 `_spawn` 函式可以將控制權從新的處理序交還給呼叫處理序。 在 `_spawn` 函式中，除非指定 `_P_OVERLAY`，否則記憶體中會同時有呼叫處理序和新處理序。 在 `_exec` 函式中，新的處理序會重疊在呼叫處理序上，因此除非嘗試開始執行新處理序時發生錯誤，否則控制權無法交還給呼叫處理序。  
  
 `_exec` 系列中函式之間的差異，以及在 `_spawn` 系列中函式之間的差異，包括找出隨新處理序執行之檔案的方法、引數傳遞給新處理序的形式，以及設定環境的方法，如下表所示。 當引數數目是常數或在編譯階段為已知時，使用傳遞引數清單的函式。 當引數數目是在執行階段決定時，使用將指標傳遞給包含引數之陣列的函式。 下表中的資訊也適用於 `_spawn` 和 `_exec` 函式的寬字元對應。  
  
### <a name="spawn-and-exec-function-families"></a>_spawn 和 _exec 函式系列  
  
|函式|使用 PATH 變數找出檔案|引數傳遞慣例|環境設定|  
|---------------|--------------------------------------|----------------------------------|--------------------------|  
|`_execl, _spawnl`|否|清單|繼承自呼叫處理序|  
|`_execle, _spawnle`|否|清單|新處理序的環境表格指標，以最後一個引數傳遞|  
|`_execlp, _spawnlp`|是|清單|繼承自呼叫處理序|  
|`_execlpe, _spawnlpe`|是|清單|新處理序的環境表格指標，以最後一個引數傳遞|  
|`_execv, _spawnv`|否|陣列|繼承自呼叫處理序|  
|`_execve, _spawnve`|否|陣列|新處理序的環境表格指標，以最後一個引數傳遞|  
|`_execvp, _spawnvp`|是|陣列|繼承自呼叫處理序|  
|`_execvpe, _spawnvpe`|是|陣列|新處理序的環境表格指標，以最後一個引數傳遞|  
  
## <a name="see-also"></a>另請參閱  
 [依類別區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)
