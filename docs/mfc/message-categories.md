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
ms.openlocfilehash: 686d5eef4aaa67785aa56133d820b637fbf4bb86
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81364746"
---
# <a name="message-categories"></a>訊息分類

您為其中編寫處理程式的種類有三個主要類別:

1. Windows 訊息

   這主要包括那些以**WM_** 首碼開頭的消息,但WM_COMMAND。 Windows 訊息是由視窗和檢視處理。 這些訊息通常會具有用來決定如何處理訊息的參數。

1. 控制通知

   這包括從控制項和其他子視窗傳送至其父視窗的 WM_COMMAND 通知訊息。 例如，當使用者採取的某項動作可能已更改編輯器控制項中文字時，編輯控制項會對其父代傳送包含 EN_CHANGE 控制項通知碼的 WM_COMMAND 訊息。 訊息的視窗處理常式會以某些適當的方式回應通知訊息，例如擷取控制項中的文字。

   框架像其他**WM_** 消息一樣路由控制通知消息。 不過，有一個例外狀況是，BN_CLICKED 控制項通知訊息是當使用者按一下按鈕時，由按鈕所傳送。 這個訊息會視為命令訊息，並且會像其他命令一樣進行傳送。

1. 命令訊息

   這包括來自使用者介面物件的 WM_COMMAND 通知訊息：功能表、工具列按鈕和快速鍵。 框架處理命令與其他消息不同,並且它們可以由更多類型的物件處理,如[命令目標中](../mfc/command-targets.md)所述。

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>視窗訊息與控制通知訊息

分類 1 和 2 中的訊息 (Windows 訊息和控制通知) 是由 Windows 處理：衍生自 `CWnd` 類別的類別物件。 這包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，以及您自己的類別 (衍生自這些基底類別)。 這類物件會封裝一個 `HWND`，即 Windows 視窗的控制代碼。

## <a name="command-messages"></a><a name="_core_command_messages"></a>命令訊息

分類 3 中的訊息 (命令) 可以由更多種類的物件進行處理：文件、文件範本和應用程式物件本身 (除了視窗和檢視之外)。 當命令會直接影響一些特定物件時，擁有命令的物件控制代碼才有意義。 例如，[檔案] 功能表上的 [開啟] 命令在邏輯上與應用程式相關：應用程式會在接收命令時開啟指定的文件。 因此 [開啟] 命令的處理常式會是應用程式類別的成員函式。 有關命令及其路由到物件的方式,請參閱[框架如何呼叫處理程式](../mfc/how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](../mfc/messages-and-commands-in-the-framework.md)
