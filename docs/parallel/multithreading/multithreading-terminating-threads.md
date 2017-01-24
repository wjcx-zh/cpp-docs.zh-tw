---
title: "多執行緒：結束執行緒 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CREATE_SUSPENDED"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "AfxEndThread 方法"
  - "多執行緒 [C++], 結束執行緒"
  - "過早的執行緒終止"
  - "啟動執行緒"
  - "停止執行緒"
  - "結束執行緒"
  - "執行緒 [C++], 停止執行緒"
  - "執行緒 [MFC], 結束執行緒"
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
caps.latest.revision: 9
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 多執行緒：結束執行緒
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

兩種正常情況會造成執行緒結束：控制函式結束或執行緒不被允許執行到完成。  如果文書處理器使用執行緒來進行背景列印，列印成功完成的話，控制函式就會正常結束。  然而，如果使用者想要取消列印，就必須不當結束背景列印執行緒。  這個主題說明如何實作每一種狀況，以及如何在執行緒終止之後取得它的結束代碼 \(Exit Code\)。  
  
-   [正常的執行緒終止](#_core_normal_thread_termination)  
  
-   [過早的執行緒終止](#_core_premature_thread_termination)  
  
-   [擷取執行緒結束代碼](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> 正常的執行緒終止  
 對於背景工作執行緒，正常的執行緒終止很簡單：結束控制函式，並且傳回一個表示終止原因的值。  您可以使用 [AfxEndThread](../Topic/AfxEndThread.md) 函式或 `return` 陳述式。  一般來說，0 表示順利完成，但這由您決定。  
  
 對於使用介面執行緒，程序一樣簡單：從使用介面執行緒內，呼叫 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)] 中的 [PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945)。  **PostQuitMessage** 取得的唯一參數是執行緒的結束代碼。  至於背景工作執行緒，0 通常表示順利完成。  
  
##  <a name="_core_premature_thread_termination"></a> 過早的執行緒終止  
 提早結束執行緒也是同樣簡單：從執行緒內呼叫 [AfxEndThread](../Topic/AfxEndThread.md)。  將想要的結束代碼當做唯一的參數傳遞。  這麼做會停止執行緒的執行、解除配置執行緒的堆疊、中斷連結所有附加到執行緒的 DLL，並從記憶體刪除執行緒物件。  
  
 `AfxEndThread` 必須從要被終止的執行緒內呼叫。  如果您要從另一個執行緒終止執行緒，您必須設定兩個執行緒之間的通訊方法。  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> 擷取執行緒結束代碼  
 若要取得背景工作執行緒或使用介面執行緒的結束代碼，呼叫 [GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190) 函式。  如需有關這個函式的詳細資訊，請參閱 [!INCLUDE[winsdkshort](../../atl/reference/includes/winsdkshort_md.md)]。  這個函式取得執行緒 \(儲存在 `CWinThread` 物件的 `m_hThread` 資料成員中\) 的控制代碼和 `DWORD` 的位址。  
  
 如果執行緒仍在作用中，**GetExitCodeThread** 會將 **STILL\_ACTIVE** 放置在提供的 `DWORD` 位址內，否則結束代碼會放置在這個位址中。  
  
 擷取 [CWinThread](../../mfc/reference/cwinthread-class.md) 物件的結束代碼需要額外的步驟。  依預設值，當 `CWinThread` 執行緒結束時，執行緒物件會被刪除。  這表示您不能存取 `m_hThread` 資料成員因為 `CWinThread` 物件已不存在。  若要避免這個狀況，請執行下列其中一種方法：  
  
-   將 `m_bAutoDelete` 資料成員設為 **FALSE**。  這會讓 `CWinThread` 物件在執行緒結束之後還能繼續存在。  然後可以在執行緒結束之後存取 `m_hThread` 資料成員。  然而，如果您使用這種技術，您要負責終結 `CWinThread`，因為架構不會自動為您刪除它。  這是優先使用的方法。  
  
-   分開儲存執行緒的控制代碼。  建立執行緒之後，將它的 `m_hThread` 資料成員 \(使用 **::DuplicateHandle**\) 複製到另一個變數，並透過這個變數來存取它。  如此一來，當發生終止時會自動刪除物件，且您仍然可以找出執行緒結束的原因。  請注意，在您可以複製控制代碼之前執行緒並沒有結束。  最安全的方式是將 **CREATE\_SUSPENDED** 傳遞到 [AfxBeginThread](../Topic/AfxBeginThread.md)，將控制代碼儲存起來，然後呼叫 [ResumeThread](../Topic/CWinThread::ResumeThread.md) 來繼續執行緒。  
  
 兩種方式都可讓您判斷 `CWinThread` 物件結束的原因。  
  
## 請參閱  
 [使用 C\+\+ 和 MFC 進行多執行緒處理](../../parallel/multithreading-with-cpp-and-mfc.md)   
 [\_endthread、\_endthreadex](../../c-runtime-library/reference/endthread-endthreadex.md)   
 [\_beginthread、\_beginthreadex](../../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)