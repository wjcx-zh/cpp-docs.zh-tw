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
ms.openlocfilehash: 1cd28a848f9be223f43412c3e0f3961cef9db6c7
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69512083"
---
# <a name="multithreading-creating-mfc-user-interface-threads"></a>多執行緒：建立 MFC 使用者介面執行緒

使用者介面執行緒通常用來處理使用者輸入，並在執行應用程式其他部分的執行緒以外，獨立回應使用者事件。 系統已為您建立並啟動主`CWinApp`應用程式執行緒（在衍生類別中提供）。 本主題描述建立額外的使用者介面執行緒所需的步驟。

您在建立使用者介面執行緒時必須做的第一件事，就是從[CWinThread](../mfc/reference/cwinthread-class.md)衍生一個類別。 您必須使用[DECLARE_DYNCREATE](../mfc/reference/run-time-object-model-services.md#declare_dyncreate)和[IMPLEMENT_DYNCREATE](../mfc/reference/run-time-object-model-services.md#implement_dyncreate)宏來宣告和執行這個類別。 這個類別必須覆寫某些函式，而且可以覆寫其他函數。 下表顯示這些函式及其應執行的工作。

### <a name="functions-to-override-when-creating-a-user-interface-thread"></a>建立使用者介面執行緒時要覆寫的函式

|函數|用途|
|--------------|-------------|
|[ExitInstance](../mfc/reference/cwinthread-class.md#exitinstance)|當執行緒終止時執行清除。 通常會覆寫。|
|[InitInstance](../mfc/reference/cwinthread-class.md#initinstance)|執行執行緒實例初始化。 必須覆寫。|
|[OnIdle](../mfc/reference/cwinthread-class.md#onidle)|執行執行緒特定的閒置時間處理。 通常不會覆寫。|
|[PreTranslateMessage](../mfc/reference/cwinthread-class.md#pretranslatemessage)|先篩選訊息，再將它們`TranslateMessage`分派`DispatchMessage`至和。 通常不會覆寫。|
|[ProcessWndProcException](../mfc/reference/cwinthread-class.md#processwndprocexception)|攔截由執行緒的訊息和命令處理常式擲回的未處理例外狀況。 通常不會覆寫。|
|[執行](../mfc/reference/cwinthread-class.md#run)|控制執行緒的函式。 包含訊息抽取。 很少遭到覆寫。|

MFC 提供兩種 `AfxBeginThread` 參數多載版本：只能建立背景工作執行緒的版本，以及可以建立使用者介面執行緒或背景工作執行緒的版本。 若要啟動您的使用者介面執行緒，請呼叫[AfxBeginThread](../mfc/reference/application-information-and-management.md#afxbeginthread)的第二個多載，並提供下列資訊：

- 衍生自之`CWinThread`類別的 [RUNTIME_CLASS](../mfc/reference/run-time-object-model-services.md#runtime_class)。

- 選擇性所需的優先權層級。 預設值為一般優先權。 如需可用優先權層級的詳細資訊，請參閱 Windows SDK 中的[SetThreadPriority](/windows/win32/api/processthreadsapi/nf-processthreadsapi-setthreadpriority) 。

- 選擇性執行緒所需的堆疊大小。 預設值與建立執行緒的大小堆疊相同。

- 選擇性CREATE_SUSPENDED，如果您想要以暫停狀態建立執行緒。 預設值為0，或正常啟動執行緒。

- 選擇性所需的安全性屬性。 預設值是與父執行緒相同的存取權。 如需有關此安全性資訊格式的詳細資訊，請參閱 Windows SDK 中的[security attributes 這個](/previous-versions/windows/desktop/legacy/aa379560\(v=vs.85\))。

`AfxBeginThread`為您執行大部分的工作。 它會建立類別的新物件、使用您提供的資訊將其初始化，並呼叫[CWinThread：： CreateThread](../mfc/reference/cwinthread-class.md#createthread)以開始執行執行緒。 整個程式中都會進行檢查，以確保在建立過程中，所有物件都已適當地解除配置。

## <a name="what-do-you-want-to-know-more-about"></a>您還想知道關於哪些方面的詳細資訊？

- [多執行緒：終止執行緒](multithreading-terminating-threads.md)

- [多執行緒：建立背景工作執行緒](multithreading-creating-worker-threads.md)

- [進程和執行緒](/windows/win32/ProcThread/processes-and-threads)

## <a name="see-also"></a>另請參閱

[使用 C++ 和 MFC 進行多執行緒處理](multithreading-with-cpp-and-mfc.md)
