---
title: "撰寫多執行緒 Win32 程式 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "通訊 [C++], 執行緒之間"
  - "多執行緒 [C++], 共用通用資源"
  - "多執行緒 [C++], 執行緒堆疊"
  - "Mutex [C++]"
  - "互斥 [C++]"
  - "資源 [C++], 多執行緒"
  - "共用資源 [C++]"
  - "堆疊 [C++]"
  - "執行緒堆疊 [C++]"
  - "執行緒 [C++], 共用通用資源"
  - "執行緒 [C++], 執行緒堆疊"
ms.assetid: 1415f47d-417f-4f42-949b-946fb28aab0e
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 撰寫多執行緒 Win32 程式
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

當您在撰寫具有多執行緒的程式時，必須協調它們的行為以及[程式資源的共用](#_core_sharing_common_resources_between_threads)。  您也必須確定每個執行緒都收到[自己的堆疊](#_core_thread_stacks)。  
  
##  <a name="_core_sharing_common_resources_between_threads"></a> 執行緒之間共同資源的共用  
  
> [!NOTE]
>  如需從 MFC 觀點出發的類似討論，請參閱[多執行緒：程式設計提示](../../parallel/multithreading-programming-tips.md)和[多執行緒：何時使用同步類別](../../parallel/multithreading-when-to-use-the-synchronization-classes.md)。  
  
 每一個執行緒都擁有自己的堆疊和自己的 CPU 暫存器的複本。  其他資源 \(例如，檔案、靜態資料和堆積記憶體\) 都是由處理序中所有執行緒共用。  使用這些共同資源的執行緒必須要同步。  Win32 提供許多方法來同步化資源，包括號誌、關鍵區段 \(Critical Section\)、事件和 Mutex。  
  
 當多重執行緒存取靜態資料時，您的程式必須處理可能的資源衝突。  試想有一個程式，其中一個執行緒會更新靜態資料結構 \(資料結構中包含將由其他執行緒顯示之項目的 *x*、*y* 座標\)。  如果更新執行緒更改了 *x* 座標，並在它變更 *y* 座標之前被優先佔用，顯示執行緒可能在 *y* 座標更新之前就被排程。  此項目可能會顯示在錯誤的位置。  您可以藉著使用號誌控制結構的存取來避免這個問題。  
  
 Mutex \(*mut*ual *ex*clusion 的縮寫\) 是在非同步執行之執行緒或處理序之間的一種通訊方式。  這種通訊通常是用來協調多重執行緒或處理序的活動，通常藉由鎖定和解除鎖定資源來控制共用資源的存取以達到目的。  若要解決這個 *x*、*y* 座標更新問題，更新執行緒會設定 Mutex，指示在執行更新之前資料結構正在使用中。  在處理兩個座標之後就會清除 Mutex。  顯示執行緒在更新顯示之前必須等候 Mutex 被清除。  等候 Mutex 的程序通常稱為 Mutex 上的封鎖，因為程序被封鎖住，在 Mutex 清除之前無法繼續。  
  
 在[多執行緒 C 程式範例](../../parallel/sample-multithread-c-program.md)中顯示的 Bounce.c 程式會使用名為 `ScreenMutex` 的 Mutex 來協調螢幕更新。  每次當其中一個顯示執行緒準備要寫入至螢幕時，它會用 `ScreenMutex` 的控制代碼和 **INFINITE** 常數來呼叫 **WaitForSingleObject**，以指示 **WaitForSingleObject** 呼叫應該透過 Mutex 進行封鎖，並且不會逾時。  如果清除 `ScreenMutex`，等候函式設定 Mutex，這樣其他的執行緒不能干擾顯示並繼續執行執行緒。  否則，執行緒會阻擋直到 Mutex 清除。  當執行緒完成顯示更新時，它會藉著呼叫 **ReleaseMutex** 來釋放 Mutex。  
  
 螢幕顯示和靜態資料只是需要小心管理的資源之中的兩種。  例如，您的程式可能有多重執行緒在存取相同的檔案。  因為另一個執行緒可能已經移動檔案指標，所以每個執行緒都必須在讀取或寫入之前重設檔案指標。  除此之外，每個執行緒必須確定在放置指標到存取檔案中間沒有被優先佔用。  這些執行緒應該使用號誌來協調對檔案的存取，藉著 **WaitForSingleObject** 和 **ReleaseMutex** 呼叫來存取每個檔案。  下列程式碼範例會說明這項技術：  
  
```  
HANDLE    hIOMutex= CreateMutex (NULL, FALSE, NULL);  
  
WaitForSingleObject( hIOMutex, INFINITE );  
fseek( fp, desired_position, 0L );  
fwrite( data, sizeof( data ), 1, fp );  
ReleaseMutex( hIOMutex);  
```  
  
##  <a name="_core_thread_stacks"></a> 執行緒堆疊  
 所有應用程式的預設堆疊空間都配置給執行的第一個執行緒，通常稱為執行緒 1。  因此，您必須指定要配置多少記憶體給您程式所需要的每一個額外執行緒的不同堆疊。  如有必要，作業系統會為執行緒配置額外的堆疊空間，但是您必須指定預設值。  
  
 `_beginthread` 呼叫裡的第一個引數是 **BounceProc** 函式的指標，這個函式會執行執行緒。  第二個引數指定執行緒的預設堆疊大小。  最後一個引數是傳遞至 **BounceProc** 的 ID 編號。  **BounceProc** 使用 ID 編號來做為亂數產生器的種子並用來選取執行緒的顏色屬性和顯示字元。  
  
 呼叫 C 的執行階段程式庫或 Win32 API 之執行緒必須讓它們所呼叫的程式庫和 API 函式擁有足夠的堆疊空間。  C 的 `printf` 函式需要超過 500 位元組的堆疊空間，而且當您呼叫 Win32 API 常式時，應該要擁有 2K 的可用堆疊空間。  
  
 因為每一個執行緒有自己的堆疊，您可以藉由盡可能使用最少的靜態資料來避免可能的資料項目碰撞。  設計您的程式來使用所有對執行緒可能是私用 \(Private\) 的資料之自動堆疊變數。  Bounce.c 程式裡中唯一全域變數是 Mutex 或在初始化後就未曾變更的變數。  
  
 Win32 也提供執行緒區域儲存區 \(Thread\-Local Storage，TLS\) 來儲存每個執行緒資料。  如需詳細資訊，請參閱[執行緒區域儲存區](../../parallel/thread-local-storage-tls.md)。  
  
## 請參閱  
 [使用 C 和 Win32 進行多執行緒處理](../../parallel/multithreading-with-c-and-win32.md)