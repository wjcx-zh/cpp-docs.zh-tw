---
title: 處理清單控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: e93e91a3219f81bf4027549fc84f1c85c8defb5b
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69507864"
---
# <a name="processing-notification-messages-in-list-controls"></a>處理清單控制項中的通知訊息

當使用者按一下資料行標頭、拖曳圖示、編輯標籤等動作時, 清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 會將通知訊息傳送至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者按一下資料行標頭時，您可能會想要根據所按資料行的內容 (例如在 Microsoft Outlook 中) 來為項目排序。

在您的 view 或 dialog 類別中處理來自清單控制項的 WM_NOTIFY 訊息。 使用屬性視窗, 根據正在處理的通知訊息, 建立具有 switch 語句的[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)處理常式函數。

如需清單控制項可以傳送至其父視窗的通知清單, 請參閱 Windows SDK 中的[清單視圖控制項參考](/windows/win32/Controls/list-view-control-reference)。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
