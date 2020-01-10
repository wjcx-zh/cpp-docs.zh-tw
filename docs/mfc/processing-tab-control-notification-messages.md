---
title: 處理索引標籤控制項通知訊息
ms.date: 11/04/2016
helpviewer_keywords:
- notifications [MFC], tab controls
- CTabCtrl class [MFC], processing notifications
- notifications [MFC], processing in CTabCtrl
- processing notifications [MFC]
- tab controls [MFC], processing notifications
ms.assetid: 758ccb7a-9e73-48f8-9073-23f7cb09918c
ms.openlocfilehash: cc322a038717d48f440df1ec571674cec80743ce
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70908068"
---
# <a name="processing-tab-control-notification-messages"></a>處理索引標籤控制項通知訊息

當使用者按一下 [索引標籤] 或 [按鈕] 時，索引標籤控制項（[CTabCtrl](../mfc/reference/ctabctrl-class.md)）會將通知訊息傳送至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 例如，當使用者按一下索引標籤時，您可能會想要在顯示網頁上的控制項資料之前，先將它設為預設值。

從您的 view 或 dialog 類別中的索引標籤控制項，處理 WM_NOTIFY 訊息。 使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，根據正在處理的通知訊息，建立具有 switch 語句的[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)處理常式函數。 如需索引標籤控制項可以傳送至其父視窗的通知清單，請參閱 Windows SDK 中索引標籤[控制項參考](/windows/win32/controls/tab-control-reference)的 [**通知**] 區段。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
