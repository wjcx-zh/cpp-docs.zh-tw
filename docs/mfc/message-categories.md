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
ms.openlocfilehash: 3875a6931b4380f0531e4c1786de6dddfccb76ca
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625473"
---
# <a name="message-categories"></a>訊息分類

您撰寫處理常式的訊息有三種主要類別：

1. Windows 訊息

   這主要包括以**WM_** 前置詞開頭的訊息，但 WM_COMMAND 除外。 Windows 訊息是由視窗和檢視處理。 這些訊息通常會具有用來決定如何處理訊息的參數。

1. 控制通知

   這包括從控制項和其他子視窗傳送至其父視窗的 WM_COMMAND 通知訊息。 例如，當使用者採取的某項動作可能已更改編輯器控制項中文字時，編輯控制項會對其父代傳送包含 EN_CHANGE 控制項通知碼的 WM_COMMAND 訊息。 訊息的視窗處理常式會以某些適當的方式回應通知訊息，例如擷取控制項中的文字。

   架構會路由控制通知訊息，如其他**WM_** 訊息。 不過，有一個例外狀況是，BN_CLICKED 控制項通知訊息是當使用者按一下按鈕時，由按鈕所傳送。 這個訊息會視為命令訊息，並且會像其他命令一樣進行傳送。

1. 命令訊息

   這包括來自使用者介面物件的 WM_COMMAND 通知訊息：功能表、工具列按鈕和快速鍵。 架構會以不同于其他訊息的方式處理命令，而且可以由更多類型的物件處理，如[命令目標](command-targets.md)中所述。

## <a name="windows-messages-and-control-notification-messages"></a><a name="_core_windows_messages_and_control.2d.notification_messages"></a>Windows 訊息和控制項通知訊息

分類 1 和 2 中的訊息 (Windows 訊息和控制通知) 是由 Windows 處理：衍生自 `CWnd` 類別的類別物件。 這包括 `CFrameWnd`、`CMDIFrameWnd`、`CMDIChildWnd`、`CView`、`CDialog`，以及您自己的類別 (衍生自這些基底類別)。 這類物件會封裝一個 `HWND`，即 Windows 視窗的控制代碼。

## <a name="command-messages"></a><a name="_core_command_messages"></a>命令訊息

分類 3 中的訊息 (命令) 可以由更多種類的物件進行處理：文件、文件範本和應用程式物件本身 (除了視窗和檢視之外)。 當命令會直接影響一些特定物件時，擁有命令的物件控制代碼才有意義。 例如，[檔案] 功能表上的 [開啟] 命令在邏輯上與應用程式相關：應用程式會在接收命令時開啟指定的文件。 因此 [開啟] 命令的處理常式會是應用程式類別的成員函式。 如需命令以及如何將其路由傳送至物件的詳細資訊，請參閱[架構如何呼叫處理常式](how-the-framework-calls-a-handler.md)。

## <a name="see-also"></a>另請參閱

[架構中的訊息和命令](messages-and-commands-in-the-framework.md)
