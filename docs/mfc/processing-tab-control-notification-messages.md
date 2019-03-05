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
ms.openlocfilehash: 4be9074f3e7d7ce4321402d27fc26283a52436e9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57267295"
---
# <a name="processing-tab-control-notification-messages"></a>處理索引標籤控制項通知訊息

當使用者按一下索引標籤或按鈕，在索引標籤控制項 ([CTabCtrl](../mfc/reference/ctabctrl-class.md)) 會傳送通知訊息至其父視窗。 如果您想要執行動作以作為回應，請處理這些訊息。 比方說，當使用者按一下索引標籤，您可能想要預設之前顯示此頁面上的控制項資料。

從您的檢視或對話方塊類別中的索引標籤控制項的處理 WM_NOTIFY 訊息。 使用 [屬性] 視窗來建立[OnChildNotify](../mfc/reference/cwnd-class.md#onchildnotify)一個 switch 陳述式的處理常式函式，根據正在處理的通知訊息。 如需索引標籤控制項可以傳送至其父視窗的通知，請參閱**通知**一節[索引標籤控制項參考](/windows/desktop/controls/tab-control-reference)Windows SDK 中。

## <a name="see-also"></a>另請參閱

[使用 CTabCtrl](../mfc/using-ctabctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
