---
title: "流程控制和環境控制 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "c.programs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "環境控制常式"
  - "父處理序"
  - "流程控制常式"
  - "處理序, 管理工作"
  - "處理序, 啟動"
  - "處理序, 停止"
ms.assetid: 7fde74c3-c2a6-4d15-84b8-092160d60c3e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# 流程控制和環境控制
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

使用程式控制的常式，開始和停止處理序從程式內。  使用環境控制常式衍生和變更有關作業系統環境的相關資訊。  
  
### 流程和環境控制函式  
  
|常式|用法|.NET Framework 對等用法|  
|--------|--------|-------------------------|  
|[abort](../c-runtime-library/reference/abort.md)|中止處理序，而不需清除緩衝區或呼叫函式是由 `atexit` 和 `_onexit`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[assert](../c-runtime-library/reference/assert-macro-assert-wassert.md)|要測試其邏輯錯誤。|[\<caps:sentence id\="tgt14" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[\_ASSERT, \_ASSERTE](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md) 巨集|與 `assert`類似，不過，只有執行階段程式庫的偵錯版本|[\<caps:sentence id\="tgt17" sentenceid\="14fd9bf776829d73028df00162f7533f" class\="tgtSentence"\>System::Diagnostics::Debug::Assert\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.debug.assert.aspx)|  
|[atexit](../c-runtime-library/reference/atexit.md)|排程執行常式在程式結束。|[\<caps:sentence id\="tgt20" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_beginthread、\_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)|若要在 Windows 作業系統處理序建立新的執行緒|[\<caps:sentence id\="tgt23" sentenceid\="221e38ecc6535bce91af4e1a19f464d1" class\="tgtSentence"\>System::Threading::Thread::Start\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.threading.thread.start.aspx)|  
|[\_cexit 。](../c-runtime-library/reference/cexit-c-exit.md)|執行 `exit` 結束程序 \(例如清除緩衝區\)，然後傳回控制權傳回給呼叫端，而不需要終止處理序。|[\<caps:sentence id\="tgt26" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process::CloseMainWindow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\_c\_exit](../c-runtime-library/reference/cexit-c-exit.md)|執行 `_exit` 結束程序，然後傳回控制權傳回給呼叫端，而不需要終止處理序。|[\<caps:sentence id\="tgt29" sentenceid\="46302f19d05c09c5875a795cb64800f9" class\="tgtSentence"\>System::Diagnostics::Process::CloseMainWindow\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.closemainwindow.aspx)|  
|[\_cwait](../c-runtime-library/reference/cwait.md)|等待直到另一個處理序終止|[\<caps:sentence id\="tgt32" sentenceid\="d9c88c429eaacaa9f37d91d29bc6504e" class\="tgtSentence"\>System::Diagnostics::Process::WaitForExit\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.waitforexit.aspx)|  
|[\_endthread、\_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)|結束 Windows 作業系統執行緒|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_execl、\_wexecl](../c-runtime-library/reference/execl-wexecl.md)|執行與引數清單的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execle、\_wexecle](../c-runtime-library/reference/execle-wexecle.md)|執行與引數清單和特定環境的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlp、\_wexeclp](../c-runtime-library/reference/execlp-wexeclp.md)|使用 `PATH` 變數和引數清單，執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execlpe、\_wexeclpe](../c-runtime-library/reference/execlpe-wexeclpe.md)|使用 `PATH` 變數，執行處理序將環境和引數清單|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execv、\_wexecv](../c-runtime-library/reference/execv-wexecv.md)|執行與引數陣列的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execve、\_wexecve](../c-runtime-library/reference/execve-wexecve.md)|執行與引數陣列和特定環境的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvp、\_wexecvp](../c-runtime-library/reference/execvp-wexecvp.md)|使用 `PATH` 變數和引數陣列，執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_execvpe、\_wexecvpe](../c-runtime-library/reference/execvpe-wexecvpe.md)|使用 `PATH` 變數，執行處理序將環境和引數陣列|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[exit](../c-runtime-library/reference/exit-exit-exit.md)|呼叫函式是由 `atexit` 和 `_onexit`，清除所有緩衝區，關閉所有開啟的檔案，並結束處理序|[\<caps:sentence id\="tgt64" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[\_exit](../c-runtime-library/reference/exit-exit-exit.md)|結束的處理序，而不呼叫 `atexit` 或 `_onexit` 或清除緩衝區|[\<caps:sentence id\="tgt67" sentenceid\="811a70e90f150f212690505b37a46c0f" class\="tgtSentence"\>System::Diagnostics::Process::Kill\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.kill.aspx)|  
|[getenv, \_wgetenv](../c-runtime-library/reference/getenv-wgetenv.md), [getenv\_s、\_wgetenv\_s](../c-runtime-library/reference/getenv-s-wgetenv-s.md)|取得環境變數的值|[\<caps:sentence id\="tgt70" sentenceid\="795988b9277d74ea3b722ecd42dcb29d" class\="tgtSentence"\>System::Environment::GetEnvironmentVariable\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.environment.getenvironmentvariable.aspx)|  
|[\_getpid](../c-runtime-library/reference/getpid.md)|取得處理序 ID 編號|[\<caps:sentence id\="tgt73" sentenceid\="745b82c461dc74b15540e9622f7cd7bd" class\="tgtSentence"\>System::Diagnostics::Process::Id\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.id.aspx)|  
|[longjmp](../c-runtime-library/reference/longjmp.md)|還原已儲存的堆疊環境;使用它執行非區域的 `goto`。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_onexit](../c-runtime-library/reference/onexit-onexit-m.md)|排程執行常式在程式結束;相容性的用途與 Microsoft C\/C\+\+ 7.0 \(含\) 以前版本|[\<caps:sentence id\="tgt81" sentenceid\="db022fa9aa2a12937c3610e3eb32e80f" class\="tgtSentence"\>System::Diagnostics::Process::Exited\<\/caps:sentence\>](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.exited.aspx)|  
|[\_pclose](../c-runtime-library/reference/pclose.md)|等待新命令處理器並關閉在關聯的管道資料流|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[perror、\_wperror](../c-runtime-library/reference/perror-wperror.md)|印出錯誤訊息|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_pipe](../c-runtime-library/reference/pipe.md)|建立用於讀取和寫入的管道|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_popen、\_wpopen](../c-runtime-library/reference/popen-wpopen.md)|建立管道並執行命令|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_putenv, \_wputenv](../c-runtime-library/reference/putenv-wputenv.md), [\_putenv\_s、\_wputenv\_s](../c-runtime-library/reference/putenv-s-wputenv-s.md)|加入或環境變數的變更值。|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[raise](../c-runtime-library/reference/raise.md)|傳送訊號至呼叫程序|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[setjmp](../c-runtime-library/reference/setjmp.md)|保存堆疊環境;使用執行非本機 `goto`|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[signal](../c-runtime-library/reference/signal.md)|控制代碼中斷信號|不適用。  若要呼叫標準 C 函式，請使用 `PInvoke`。  如需詳細資訊，請參閱[平台叫用範例](../Topic/Platform%20Invoke%20Examples.md)。|  
|[\_spawnl、\_wspawnl](../c-runtime-library/reference/spawnl-wspawnl.md)|建立和執行與指定引數清單中的處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnle、\_wspawnle](../c-runtime-library/reference/spawnle-wspawnle.md)|建立並執行指定的引數清單和環境的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlp、\_wspawnlp](../c-runtime-library/reference/spawnlp-wspawnlp.md)|使用 `PATH` 變數和指定的引數清單，建立和執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnlpe、\_wspawnlpe](../c-runtime-library/reference/spawnlpe-wspawnlpe.md)|使用 `PATH` 指定的變數和引數清單，建立和執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnv、\_wspawnv](../c-runtime-library/reference/spawnv-wspawnv.md)|建立和執行與指定引數陣列中的處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnve、\_wspawnve](../c-runtime-library/reference/spawnve-wspawnve.md)|建立並執行指定的引數陣列和環境的新處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvp、\_wspawnvp](../c-runtime-library/reference/spawnvp-wspawnvp.md)|使用 `PATH` 變數和指定的引數陣列，建立和執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[\_spawnvpe、\_wspawnvpe](../c-runtime-library/reference/spawnvpe-wspawnvpe.md)|使用 `PATH` 指定的變數和引數陣列，建立和執行處理序|[System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)， [System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)|  
|[system、\_wsystem](../c-runtime-library/reference/system-wsystem.md)|執行作業系統的命令|[System::Diagnostics::ProcessStartInfo 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.processstartinfo.aspx)， [System::Diagnostics::Process 類別](https://msdn.microsoft.com/en-us/library/system.diagnostics.process.aspx)|  
  
 在 Windows 作業系統中，產生的流程與產生的處理序相同。  任何處理序都可以使用 `_cwait` 等候處理序 ID 知道的其他處理序。  
  
 在 `_exec` 和 `_spawn` 家族之間的差異在於 `_spawn` 函式可傳回從處理序的控制項加入至呼叫程序。  在 `_spawn` 函式中，除非已指定 `_P_OVERLAY` ，呼叫處理和處理序是存在於記憶體中。  在 `_exec` 函式，更新過程覆疊呼叫程序，因此，控制項無法回到呼叫程序，除非錯誤在嘗試產生啟動新的處理序的執行。  
  
 區別在 `_exec` 系列的函式中，以及在那些中 `_spawn` 家族，涉及尋找當做引數傳遞給處理序的處理序、表單和設定環境方法所執行的檔案方法，如下表所示。  使用引數清單的函式，當引數數目是常數或在編譯時間。  使用將指標傳遞給包含引數的陣列的函式，當引數數目要判斷在執行階段時。  資訊下表中也適用於 `_spawn` 和 `_exec` 函式的寬字元對應。  
  
### \_spawn 函式家族和 \_exec  
  
|函式|使用路徑變數尋找檔案。|引數傳遞慣例|環境設定|  
|--------|-----------------|------------|----------|  
|`_execl, _spawnl`|沒有|List|繼承自呼叫處理序|  
|`_execle, _spawnle`|沒有|List|對環境資料表的指標做為引數傳遞的最後一個處理序的|  
|`_execlp, _spawnlp`|有|List|繼承自呼叫處理序|  
|`_execlpe, _spawnlpe`|有|List|對環境資料表的指標做為引數傳遞的最後一個處理序的|  
|`_execv, _spawnv`|沒有|陣列|繼承自呼叫處理序|  
|`_execve, _spawnve`|沒有|陣列|對環境資料表的指標做為引數傳遞的最後一個處理序的|  
|`_execvp, _spawnvp`|有|陣列|繼承自呼叫處理序|  
|`_execvpe, _spawnvpe`|有|陣列|對環境資料表的指標做為引數傳遞的最後一個處理序的|  
  
## 請參閱  
 [依分類區分的執行階段常式](../c-runtime-library/run-time-routines-by-category.md)