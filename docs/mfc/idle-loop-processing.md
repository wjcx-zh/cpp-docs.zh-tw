---
title: 閒置迴圈處理
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, background processing
- PeekMessage method [MFC], elsewhere than message loop
- PeekMessage method [MFC]
- MFC, messages
- messages [MFC], loops
- OnIdle method [MFC]
- processing [MFC], background
- idle loop processing [MFC]
- idle processing [MFC]
- threading [MFC], alternatives to multithreading
- processing, during idle loop
- processing [MFC]
- background processing [MFC]
ms.assetid: 5c7c46c1-6107-4304-895f-480983bb1e44
ms.openlocfilehash: 9579d4bb8768b0227453af401d6fdc8a8bd482b4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376005"
---
# <a name="idle-loop-processing"></a>閒置迴圈處理

許多應用程式會「在背景」進行耗時的處理。 有時候會因為效能考量而使用多執行緒進行此類工作。 線程涉及額外的開發開銷,因此不建議它們執行簡單任務,如 MFC 在[OnIdle](../mfc/reference/cwinthread-class.md#onidle)函數中所做的空閒時間工作。 本文會著重於閒置處理的部分。 有關多線程的詳細資訊,請參閱[多線緒主題](../parallel/multithreading-support-for-older-code-visual-cpp.md)。

某些種類的背景處理適合在使用者與應用程式沒有互動的期間完成。 在針對 Microsoft Windows 作業系統所開發的應用程式中，應用程式可以藉由將耗時的處理序分割成許多小片段來執行閒置時間處理。 處理每個片段後,應用程式使用[PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew)迴圈向Windows生成執行控制。

本文說明兩種可在應用程式中進行閒置處理的方式：

- 在 MFC 的主消息迴圈中使用**PeekMessage。**

- 在應用程式中的其他地方嵌入另一個**PeekMessage**迴圈。

## <a name="peekmessage-in-the-mfc-message-loop"></a><a name="_core_peekmessage_in_the_mfc_message_loop"></a>在 MFC 訊息循環中窺視訊息

在使用 MFC 開發的應用程式`CWinThread`中, 類別中的主訊息迴圈包含一個訊息迴圈,該消息循環稱為[PeekMessage](/windows/win32/api/winuser/nf-winuser-peekmessagew) Win32 API。 這個迴圈也會在各個訊息之間呼叫 `OnIdle` 的 `CWinThread` 成員函式。 應用程式可以藉由覆寫 `OnIdle` 函式，在閒置時間處理這些訊息。

> [!NOTE]
> `Run``OnIdle`,和某些其他成員函數現在是類`CWinThread`的成員,而不是`CWinApp`類的成員。 `CWinApp` 衍生自 `CWinThread`。

有關執行空閒處理的詳細資訊,請參閱*MFC 參考*中的[OnIdle。](../mfc/reference/cwinthread-class.md#onidle)

## <a name="peekmessage-elsewhere-in-your-application"></a><a name="_core_peekmessage_elsewhere_in_your_application"></a>在應用程式中的其他地方窺視訊息

在應用程式中執行閒置處理的另一種方法包含將訊息迴圈內嵌在您的某個函式中。 此消息迴圈與 MFC 的主消息迴圈非常相似,該迴圈位於[CWinThread::run](../mfc/reference/cwinthread-class.md#run)中。 這表示在使用 MFC 開發的應用程式中，這類迴圈必須執行許多和主要訊息迴圈相同的函式。 下列程式碼片段說明如何撰寫與 MFC 相容的訊息迴圈：

[!code-cpp[NVC_MFCDocView#8](../mfc/codesnippet/cpp/idle-loop-processing_1.cpp)]

這個嵌入在函式中的程式碼，會在需要執行閒置處理時執行迴圈。 在該循環中,巢狀重複呼叫`PeekMessage`。 只要該呼叫傳回非零的值，迴圈就會呼叫 `CWinThread::PumpMessage` 執行一般訊息轉譯和分派。 雖然 `PumpMessage` 並未記載，但您可以檢查 Visual C++ 安裝的 \atlmfc\src\mfc 目錄中，ThrdCore.Cpp 檔案的原始程式碼。

一旦內部迴圈結束，外部迴圈便會搭配一個或多個對 `OnIdle` 的呼叫以執行閒置處理。 第一次呼叫是供 MFC 使用。 您可以建立其他對 `OnIdle` 的呼叫，以完成您的背景工作。

有關執行空閒處理的詳細資訊,請參閱 MFC 庫參考中的[OnIdle。](../mfc/reference/cwinthread-class.md#onidle)

## <a name="see-also"></a>另請參閱

[一般 MFC 主題](../mfc/general-mfc-topics.md)
