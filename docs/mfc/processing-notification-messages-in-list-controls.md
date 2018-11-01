---
title: 處理清單控制項中的通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- processing notifications [MFC]
- CListCtrl class [MFC], processing notifications
ms.assetid: 1f0e296e-d2a3-48fc-ae38-51d7fb096f51
ms.openlocfilehash: 427abe5259334588b566656abd70acf22b923809
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50490086"
---
# <a name="processing-notification-messages-in-list-controls"></a>處理清單控制項中的通知訊息

當使用者按一下資料行標頭、 拖曳圖示、 編輯標籤等等，清單控制項 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 會傳送通知訊息至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者按一下資料行標頭時，您可能會想要根據所按資料行的內容 (例如在 Microsoft Outlook 中) 來為項目排序。

從清單控制項，檢視或對話方塊類別中的處理 WM_NOTIFY 訊息。 使用 [屬性] 視窗來建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)一個 switch 陳述式的處理常式函式，根據正在處理的通知訊息。

如需清單控制項可以傳送至其父視窗的通知，請參閱[清單檢視控制項參考](/windows/desktop/Controls/list-view-control-reference)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

