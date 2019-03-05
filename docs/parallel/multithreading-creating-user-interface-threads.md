---
title: 多執行緒：建立 MFC 使用者介面執行緒
ms.date: 08/27/2018
f1_keywords:
- CREATE_SUSPENDED
- SECURITY_ATTRIBUTES
helpviewer_keywords:
- multithreading [C++], user interface threads
- threading [C++], creating threads
- threading [C++], user interface threads
- user interface threads [C++]
- threading [MFC], user interface threads
ms.assetid: 446925c1-db59-46ea-ae5b-d5ae5d5b91d8
ms.openlocfilehash: ac22fad95041b07e132d31a2d246e58c3b40d30c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57293312"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>多執行緒：建立 MFC 使用者介面執行緒

使用者介面執行緒通常會用來處理使用者輸入，並回應使用者事件，獨立執行的應用程式其他部分的執行緒中。 主應用程式執行緒 (中提供您`CWinApp`-衍生的類別) 已建立並啟動。 本主題說明建立其他的使用者介面執行緒的必要步驟。

建立使用者介面執行緒時，您必須執行的第一件事就是衍生的類別[CWinThread](../mfc/reference/cwinthread-class.md)。 您必須宣告並實作此類別，使用[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)並[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)巨集。 這個類別必須覆寫某些函式，而且可以覆寫其他人。 這些函式，它們應該採取下表所示。

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>若要建立使用者介面執行緒時覆寫的函式

|功能|用途|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|當執行緒終止時，請執行清除作業。 通常覆寫。|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|執行執行緒的執行個體初始化。 必須覆寫。|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|執行特定執行緒的閒置時間處理。 通常不覆寫。|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|篩選訊息，再將它們分派至`TranslateMessage`和`DispatchMessage`。 通常不覆寫。|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|攔截未處理的執行緒的訊息和命令處理常式所擲回的例外狀況。 通常不覆寫。|
|[執行](../mfc/reference/cwinthread-class.md#run)|控制執行緒的函式。 包含訊息幫浦。 很少覆寫。|

MFC 提供兩種 `AfxBeginThread` 參數多載版本：只能建立背景工作執行緒的版本，以及可以建立使用者介面執行緒或背景工作執行緒的版本。 若要啟動您的使用者介面執行緒，呼叫的第二個多載[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)，提供下列資訊：

- [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)類別衍生自的`CWinThread`。

- （選擇性）所需的優先權層級。 預設值是一般優先權。 如需可用的優先權層級的詳細資訊，請參閱[SetThreadPriority](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) Windows SDK 中。

- （選擇性）執行緒所需的堆疊大小。 預設值是相同的大小堆疊，與建立的執行緒。

- （選擇性）如果您想要在暫停狀態中建立的執行緒，CREATE_SUSPENDED。 預設值為 0，或以正常方式啟動執行緒。

- （選擇性）所需的安全性屬性。 預設為與父執行緒相同的存取權。 此安全性資訊的格式的相關資訊，請參閱[SECURITY_ATTRIBUTES](https://msdn.microsoft.com/library/windows/desktop/aa379560) Windows SDK 中。

`AfxBeginThread` 為您做了大部分的工作。 它會建立您的類別的新物件，使用您提供的資訊，並呼叫它初始化[CWinThread::CreateThread](../mfc/reference/cwinthread-class.md#createthread)開始執行執行緒。 整個程序進行檢查以確定所有物件都是已解除配置正確建立的任何部分萬一失敗。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [多執行緒：終止執行緒](multithreading-terminating-threads.md)

- [多執行緒：建立背景工作執行緒](multithreading-creating-worker-threads.md)

- [處理序和執行緒](/windows/desktop/ProcThread/processes-and-threads)

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
