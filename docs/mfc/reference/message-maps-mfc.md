---
title: 訊息對應 (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 4305d9b1db297eebcb189d2fad98b8c634ed1133
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908045"
---
# <a name="message-maps-mfc"></a>訊息對應 (MFC)

此參考的這個區段會列出所有[訊息對應宏](../../mfc/reference/message-map-macros-mfc.md)和所有[CWnd](../../mfc/reference/cwnd-class.md)訊息對應專案，以及對應的成員函式原型：

|Category|說明|
|--------------|-----------------|
|ON\_命令訊息處理常式|處理`WM_COMMAND`使用者功能表選取專案或功能表存取金鑰所產生的訊息。|
|[子視窗通知訊息處理常式](../../mfc/reference/child-window-notification-message-handlers.md)|處理來自子視窗的通知訊息。|
|[WM_ 訊息處理常式](../../mfc/reference/handlers-for-wm-messages.md)|處理`WM_`訊息， `WM_PAINT`例如。|
|[使用者定義的訊息處理常式](../../mfc/reference/user-defined-handlers.md)|處理使用者定義的訊息。|

（如需此參考中使用之術語和慣例的說明，請參閱[如何使用訊息對應交互參考](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)）。

由於 Windows 是以訊息為導向的作業系統，因此 Windows 環境的大部分程式設計工作都牽涉到訊息處理。 每次發生按鍵或滑鼠按下的事件時，就會傳送一則訊息給應用程式，接著就必須處理該事件。

MFC 程式庫提供針對以訊息為基礎之程式設計優化的程式設計模型。 在此模型中，「訊息對應」是用來指定哪些函式會處理特定類別的各種訊息。 訊息對應包含一或多個宏，指定哪些函式會處理哪些訊息。 例如，包含`ON_COMMAND`宏的訊息對應可能看起來像這樣：

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

`ON_COMMAND`宏是用來處理功能表、按鈕和快速鍵所產生的命令訊息。 [宏](../../mfc/reference/message-map-macros-mfc.md)可用於對應下列各項：

## <a name="windows-messages"></a>Windows 訊息

- 控制通知

- 使用者定義的訊息

## <a name="command-messages"></a>命令訊息

- 已註冊的使用者自訂訊息

- 使用者介面更新訊息

## <a name="ranges-of-messages"></a>訊息範圍

- 命令

- 更新處理常式訊息

- 控制通知

雖然訊息對應宏很重要，但您通常不需要直接使用它們。 這是因為當您使用它來建立訊息處理函式與訊息的關聯時，[類別 Wizard](mfc-class-wizard.md)會自動在您的原始程式檔中建立訊息對應專案。 每當您想要編輯或加入訊息對應專案時，都可以使用類別 Wizard。

> [!NOTE]
>  類別 Wizard 不支援訊息對應範圍。 您必須自行撰寫這些訊息對應專案。

不過，訊息對應是 MFC 程式庫的重要部分。 您應該瞭解他們的功能，並提供檔給他們。

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
