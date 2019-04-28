---
title: 訊息分類
ms.date: 11/04/2016
helpviewer_keywords:
- messages [MFC], categories
- control-notification messages [MFC]
- Windows messages [MFC], categories
- controls [MFC], notifications
- command messages [MFC]
- messages [MFC], Windows
- message handling [MFC], message types
ms.assetid: 68e1db75-9da6-4a4d-b2c2-dc4d59f8d87b
ms.openlocfilehash: 07d9e706e8ed01a81ee580e7c4e11fa1f1a7a8df
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62206876"
---
# <a name="message-categories"></a>訊息分類

哪些種類的訊息您撰寫處理常式為三個主要類別：

1. Windows 訊息

   這包括主要是在開頭的訊息**WM_** 前置詞，除了 WM_COMMAND。 Windows 訊息是由視窗和檢視處理。 這些訊息通常會具有用來決定如何處理訊息的參數。

1. 控制項通知

   這包括控制項和其他子視窗從其父視窗的 WM_COMMAND 通知訊息。 例如，編輯控制項其父代傳送包含 EN_CHANGE 控制項通知程式碼，當使用者採取的動作，可能已變更編輯控制項中的文字的 WM_COMMAND 訊息。 訊息的視窗處理常式會以某些適當的方式回應通知訊息，例如擷取控制項中的文字。

   架構會將這類其他的控制項通知訊息的路由**WM_** 訊息。 一個例外狀況，不過，是當使用者按一下時，由按鈕所傳送的 BN_CLICKED 控制項通知訊息。 這個訊息會視為命令訊息，並且會像其他命令一樣進行傳送。

1. 命令訊息

   這包括從使用者介面物件的 WM_COMMAND 通知訊息： 功能表、 工具列按鈕和快速鍵。 Framework 處理其他訊息，與不同的命令，並能夠處理由多種類型的物件中所述[命令目標](../mfc/command-targets.md)。

##  <a name="_core_windows_messages_and_control.2d.notification_messages"></a> Windows 訊息和控制項通知訊息

分類 1 和 2 中的訊息 (Windows 訊息和控制通知) 是由 Windows 處理：衍生自 `CWnd` 類別的類別物件。 這包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，以及您自己的類別 (衍生自這些基底類別)。 這類物件會封裝一個 `HWND`，即 Windows 視窗的控制代碼。

##  <a name="_core_command_messages"></a> 命令訊息

分類 3 中的訊息 (命令) 可以由更多種類的物件進行處理：文件、文件範本和應用程式物件本身 (除了視窗和檢視之外)。 當命令會直接影響一些特定物件時，擁有命令的物件控制代碼才有意義。 例如，[檔案] 功能表上的 [開啟] 命令在邏輯上與應用程式相關：應用程式會在接收命令時開啟指定的文件。 因此 [開啟] 命令的處理常式會是應用程式類別的成員函式。 如需詳細資訊命令和物件的路由方式，請參閱 <<c0> [ 架構如何呼叫處理常式](../mfc/how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)
