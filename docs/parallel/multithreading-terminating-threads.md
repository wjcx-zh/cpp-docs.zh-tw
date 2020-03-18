---
title: 多執行緒：在 MFC 中終止執行緒
ms.date: 08/27/2018
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
ms.openlocfilehash: 60c60d1aedf19ade6c84dafacd7de7a2e650e6ca
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446278"
---
# <a name="multithreading-terminating-threads-in-mfc"></a>多執行緒：在 MFC 中終止執行緒

兩個正常情況會造成執行緒終止：控制函式會結束，或不允許執行緒執行到完成。 如果字處理器使用執行緒來進行背景列印，則在列印成功完成時，控制函式會正常終止。 不過，如果使用者想要取消列印，背景列印執行緒必須提前終止。 本主題說明如何執行每種情況，以及如何線上程終止之後取得其結束代碼。

- [一般執行緒終止](#_core_normal_thread_termination)

- [過早的執行緒終止](#_core_premature_thread_termination)

- [抓取執行緒的結束代碼](#_core_retrieving_the_exit_code_of_a_thread)

## <a name="_core_normal_thread_termination"></a>一般執行緒終止

若是背景工作執行緒，一般執行緒終止很簡單：結束控制函式，並傳回表示終止原因的值。 您可以使用[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread)函數或**return**語句。 通常，0表示成功完成，但這是由您負責。

就使用者介面執行緒而言，此程式就像簡單的：從使用者介面執行緒內，在 Windows SDK 中呼叫[PostQuitMessage](/windows/win32/api/winuser/nf-winuser-postquitmessage) 。 `PostQuitMessage` 所採用的唯一參數是執行緒的結束代碼。 就工作者執行緒而言，0通常表示成功完成。

## <a name="_core_premature_thread_termination"></a>過早的執行緒終止

將執行緒提前終止幾乎是簡單的：從執行緒內呼叫[AfxEndThread](../mfc/reference/application-information-and-management.md#afxendthread) 。 傳遞所需的結束代碼作為唯一的參數。 這會停止執行執行緒、取消配置執行緒的堆疊、卸離附加至執行緒的所有 Dll，並從記憶體中刪除線程物件。

必須從要終止的執行緒內呼叫 `AfxEndThread`。 如果您想要從另一個執行緒終止執行緒，您必須在兩個執行緒之間設定通訊方法。

## <a name="_core_retrieving_the_exit_code_of_a_thread"></a>抓取執行緒的結束代碼

若要取得背景工作角色或使用者介面執行緒的結束代碼，請呼叫[GetExitCodeThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-getexitcodethread)函式。 如需此函數的詳細資訊，請參閱 Windows SDK。 此函式會採用執行緒的控制碼（儲存在 `CWinThread` 物件的 `m_hThread` 資料成員中）和 DWORD 的位址。

如果執行緒仍在使用中，`GetExitCodeThread` 會將 STILL_ACTIVE 放在所提供的 DWORD 位址中;否則，結束代碼就會放在此位址中。

抓取[CWinThread](../mfc/reference/cwinthread-class.md)物件的結束代碼需要額外的步驟。 根據預設，當 `CWinThread` 執行緒終止時，會刪除 thread 物件。 這表示您無法存取 `m_hThread` 資料成員，因為 `CWinThread` 物件已不存在。 若要避免這種情況，請執行下列其中一項動作：

- 將 `m_bAutoDelete` 資料成員設定為 FALSE。 這可讓 `CWinThread` 物件線上程終止之後存留下來。 接著，您可以線上程終止之後存取 `m_hThread` 資料成員。 不過，如果您使用這項技術，就必須負責終結 `CWinThread` 物件，因為架構不會自動為您刪除它。 這是慣用的方法。

- 分別儲存執行緒的控制碼。 建立執行緒之後，將其 `m_hThread` 資料成員（使用 `::DuplicateHandle`）複製到另一個變數，並透過該變數加以存取。 如此一來，當終止發生時，就會自動刪除物件，而您仍然可以找出執行緒終止的原因。 請注意，在您可以複製控制碼之前，執行緒不會終止。 若要這麼做，最安全的方式是將 CREATE_SUSPENDED 傳遞至[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)、儲存控制碼，然後藉由呼叫[ResumeThread](../mfc/reference/cwinthread-class.md#resumethread)來繼續執行緒。

任一種方法都可讓您判斷 `CWinThread` 物件終止的原因。

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)<br/>
[_endthread、_endthreadex](../c-runtime-library/reference/endthread-endthreadex.md)<br/>
[_beginthread、_beginthreadex](../c-runtime-library/reference/beginthread-beginthreadex.md)<br/>
[ExitThread](/windows/win32/api/processthreadsapi/nf-processthreadsapi-exitthread)
