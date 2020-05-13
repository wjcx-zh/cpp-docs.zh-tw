---
title: 訊息對應 (MFC)
ms.date: 09/07/2019
helpviewer_keywords:
- message maps [MFC], MFC
- Windows messages [MFC], message maps
- messages [MFC], Windows
- MFC, messages
ms.assetid: 3f9855e4-9d7d-4b64-8f3f-a19ea3cf79ba
ms.openlocfilehash: 8080becf1a1a153322bfd03cbd7006eaf2ce4e13
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81356581"
---
# <a name="message-maps-mfc"></a>訊息對應 (MFC)

引用的這一部分列出了所有[消息映射宏](../../mfc/reference/message-map-macros-mfc.md)和所有[CWnd](../../mfc/reference/cwnd-class.md)消息映射項目以及相應的成員函數原型:

|類別|描述|
|--------------|-----------------|
|開啟\_COMMAND 訊息處理程式|處理`WM_COMMAND`用戶功能表選擇或功能表存取鍵生成的消息。|
|[子視窗通知訊息處理常式](../../mfc/reference/child-window-notification-message-handlers.md)|處理來自子視窗的通知消息。|
|[WM_訊息處理常式](../../mfc/reference/handlers-for-wm-messages.md)|處理`WM_`訊息,如`WM_PAINT`。|
|[使用者定義的訊息處理程式](../../mfc/reference/user-defined-handlers.md)|處理使用者定義的消息。|

(有關此參考中使用的術語和約定的說明,請參閱[如何使用消息映射交叉引用](../../mfc/reference/how-to-use-the-message-map-cross-reference.md)。

由於 Windows 是面向消息的作業系統,因此 Windows 環境的大部分程式設計涉及消息處理。 每次發生按鍵或滑鼠按一下等事件時,都會向應用程式發送消息,應用程式必須處理該事件。

Microsoft 基礎類庫提供了針對基於消息的程式設計最佳化的程式設計模型。 在此模型中,「消息映射」用於指定哪些函數將處理特定類的各種消息。 消息映射包含一個或多個宏,用於指定哪些消息將由哪些函數處理。 例如,包含`ON_COMMAND`宏的消息映射可能如下所示:

[!code-cpp[NVC_MFCMessageMaps#16](../../mfc/reference/codesnippet/cpp/message-maps-mfc_1.cpp)]

該`ON_COMMAND`宏用於處理由功能表、按鈕和快速鍵生成的命令訊息。 [巨集](../../mfc/reference/message-map-macros-mfc.md)可用於對應以下內容:

## <a name="windows-messages"></a>視窗訊息

- 控制通知

- 使用者定義的訊息

## <a name="command-messages"></a>命令訊息

- 已註冊使用者定義的訊息

- 使用者介面更新訊息

## <a name="ranges-of-messages"></a>訊息範圍

- 命令

- 更新處理常式訊息

- 控制通知

儘管消息映射宏很重要,但通常不必直接使用它們。 這是因為[類嚮導](mfc-class-wizard.md)在使用源檔中自動創建消息映射條目,將消息處理函數與消息相關聯。 任何時候要編輯或添加消息映射條目時,都可以使用類嚮導。

> [!NOTE]
> 類嚮導不支援消息映射範圍。 您必須自己編寫這些消息映射條目。

但是,消息映射是Microsoft基礎類庫的重要組成部分。 您應該瞭解它們做什麼,並為它們提供文檔。

## <a name="see-also"></a>另請參閱

[結構、樣式、回呼和訊息對應](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)
