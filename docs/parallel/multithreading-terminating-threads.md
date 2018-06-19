---
title: 多執行緒： 結束執行緒 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
f1_keywords:
- CREATE_SUSPENDED
dev_langs:
- C++
helpviewer_keywords:
- premature thread termination
- starting threads
- threading [MFC], terminating threads
- multithreading [C++], terminating threads
- threading [C++], stopping threads
- terminating threads
- stopping threads
- AfxEndThread method
ms.assetid: 4c0a8c6d-c02f-456d-bd02-0a8c8d006ecb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9376e9f8c9e9d74d88d0bef40dc71fd43d51f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689580"
---
# <a name="multithreading-terminating-threads"></a>多執行緒：結束執行緒
有兩種一般情況會導致執行緒終止： 控制函式會結束，或不允許執行緒執行到完成為止。 如果文書處理器用於列印背景的執行緒，控制函式就會在列印成功完成的話正常結束。 如果使用者想要取消列印，不過，有提前終止列印背景的執行緒。 本主題說明如何實作每種情況以及如何終止之後取得執行緒的結束代碼。  
  
-   [正常的執行緒終止](#_core_normal_thread_termination)  
  
-   [過早的執行緒終止](#_core_premature_thread_termination)  
  
-   [擷取執行緒的結束代碼](#_core_retrieving_the_exit_code_of_a_thread)  
  
##  <a name="_core_normal_thread_termination"></a> 正常的執行緒終止  
 背景工作執行緒，正常的執行緒終止很簡單： 結束控制函式，並傳回值，表示終止的原因。 您可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函式或`return`陳述式。 一般而言，0 表示成功完成，但這是由您決定。  
  
 使用者介面執行緒，處理程序也一樣簡單： 從使用者介面執行緒中呼叫[PostQuitMessage](http://msdn.microsoft.com/library/windows/desktop/ms644945)中[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 唯一的參數， **PostQuitMessage**採用是執行緒的結束代碼。 對於背景工作執行緒，0，通常表示順利完成。  
  
##  <a name="_core_premature_thread_termination"></a> 過早的執行緒終止  
 提前終止執行緒是幾乎一樣簡單： 呼叫[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)從執行緒內。 傳遞所需的結束代碼做為唯一參數。 這會停止執行緒的執行、 取消配置執行緒的堆疊、 中斷連結附加至執行緒的所有 Dll 和從記憶體刪除執行緒物件。  
  
 `AfxEndThread` 必須從呼叫終止執行緒內。 如果您想要終止其他執行緒的執行緒，您必須設定兩個執行緒之間的通訊方法。  
  
##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> 擷取執行緒的結束代碼  
 若要取得使用者介面執行緒或背景工作的結束代碼，請呼叫[GetExitCodeThread](http://msdn.microsoft.com/library/windows/desktop/ms683190)函式。 此函式的相關資訊，請參閱[!INCLUDE[winsdkshort](../atl-mfc-shared/reference/includes/winsdkshort_md.md)]。 此函式的控制代碼的執行緒 (儲存在`m_hThread`資料成員`CWinThread`物件) 的地址`DWORD`。  
  
 如果仍在作用中，執行緒**GetExitCodeThread**放置**STILL_ACTIVE**所提供`DWORD`位址; 否則結束代碼會置於這個地址。  
  
 擷取的結束代碼[CWinThread](../mfc/reference/cwinthread-class.md)物件會採用額外的步驟。 根據預設，當`CWinThread`執行緒終止，執行緒物件，會刪除。 這表示您無法存取`m_hThread`資料成員因為`CWinThread`物件不再存在。 若要避免這種情況下，執行下列其中一項：  
  
-   設定`m_bAutoDelete`資料成員，才能**FALSE**。 這可讓`CWinThread`存留在執行緒終止之後的物件。 然後您可以存取`m_hThread`執行緒終止之後的資料成員。 如果您使用這項技術，不過，您必須負責終結`CWinThread`物件，因為架構不會自動刪除它為您。 這是慣用的方法。  
  
-   個別存放區的執行緒控制代碼。 執行緒建立之後，請複製它`m_hThread`資料成員 (使用 **:: DuplicateHandle**) 給另一個變數，並利用該變數存取它。 當終止時，而您仍然可以找出執行緒結束的原因，會自動刪除此物件的方式。 請小心執行緒並不會終止之前，您可以複製的控制代碼。 若要這樣做最安全的方法是傳遞**CREATE_SUSPENDED**至[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，存放區控制代碼，然後繼續執行緒藉由呼叫[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)。  
  
 這兩種方法可讓您判斷為什麼`CWinThread`終止的物件。  
  
## <a name="see-also"></a>另請參閱  
 [使用 c + + 和 MFC 進行多執行緒處理](../parallel/multithreading-with-cpp-and-mfc.md)   
 [_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)   
 [_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)   
 [ExitThread](http://msdn.microsoft.com/library/windows/desktop/ms682659)