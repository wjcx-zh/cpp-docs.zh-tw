---
title: 多執行緒： 結束在 MFC 中的執行緒
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
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
ms.openlocfilehash: c92d95bc2aa63d78c98d10e25de79344fe1ee0f0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50484012"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>多執行緒： 結束在 MFC 中的執行緒

兩種正常情況會造成執行緒結束： 結束控制函式，或不允許執行緒執行到完成為止。 如果文書處理器使用執行緒來進行背景列印，控制函式就會在列印成功完成正常結束。 如果使用者想要取消列印，不過，有必須不當結束背景列印執行緒。 本主題說明如何實作每種情況，以及如何終止之後取得執行緒的結束代碼。

- [正常的執行緒終止](#_core_normal_thread_termination)

- [過早的執行緒終止](#_core_premature_thread_termination)

- [擷取執行緒的結束代碼](#_core_retrieving_the_exit_code_of_a_thread)

##  <a name="_core_normal_thread_termination"></a> 正常的執行緒終止

對於背景工作執行緒，正常的執行緒終止很簡單： 結束控制函式，並傳回值，表示終止的原因。 您可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函式或**傳回**陳述式。 一般而言，0 表示順利完成，但這由您決定。

使用者介面執行緒，程序也一樣簡單： 從使用者介面執行緒內呼叫[PostQuitMessage](https://msdn.microsoft.com/library/windows/desktop/ms644945) Windows SDK 中。 唯一的參數，`PostQuitMessage`會是執行緒的結束代碼。 至於背景工作執行緒，0 通常表示順利完成。

##  <a name="_core_premature_thread_termination"></a> 過早的執行緒終止

提早結束執行緒也是一樣簡單： 呼叫[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)從執行緒內。 傳遞所需的結束代碼當做唯一的參數。 這會停止執行執行緒、 解除配置執行緒的堆疊、 中斷連結所有附加至執行緒，Dll 和從記憶體刪除執行緒物件。

`AfxEndThread` 必須從內呼叫的執行緒終止。 如果您想要終止其他執行緒的執行緒，您必須設定兩個執行緒之間的通訊方法。

##  <a name="_core_retrieving_the_exit_code_of_a_thread"></a> 擷取執行緒的結束代碼

若要取得背景工作角色或使用者介面執行緒的結束代碼，請呼叫[GetExitCodeThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)函式。 如需此函式的資訊，請參閱 Windows SDK。 此函式控制代碼的執行緒 (儲存在`m_hThread`資料成員`CWinThread`物件) 以及 DWORD 的位址。

如果執行緒仍在作用中， `GetExitCodeThread` STILL_ACTIVE 置於所提供的 DWORD 位址; 否則放置在這個位址的結束代碼。

擷取的結束代碼[CWinThread](../mfc/reference/cwinthread-class.md)物件需要額外的步驟。 根據預設，當`CWinThread`執行緒結束時，會刪除執行緒物件。 這表示您無法存取`m_hThread`資料成員因為`CWinThread`物件不再存在。 若要避免這種情況下，執行下列其中一項動作：

- 設定`m_bAutoDelete`資料成員設為 FALSE。 這可讓`CWinThread`物件在執行緒結束之後。 然後您可以存取`m_hThread`執行緒結束之後的資料成員。 如果您使用這項技術，不過，您必須負責終結`CWinThread`物件，因為架構將不會自動為您刪除它。 這是慣用的方法。

- 分開儲存執行緒的控制代碼。 建立執行緒之後，複製其`m_hThread`資料成員 (使用`::DuplicateHandle`) 給另一個變數並利用該變數來存取它。 當終止會發生，且您仍然可以找出執行緒結束的原因時，會自動刪除這種方式的物件。 請小心之前您可以複製控制代碼，並不會終止執行緒。 若要這樣做最安全的方法是將傳遞至 CREATE_SUSPENDED [AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，和儲存控制代碼，然後繼續藉由呼叫的執行緒[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)。

這兩種方法可讓您判斷為什麼`CWinThread`終止的物件。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-exitthread)