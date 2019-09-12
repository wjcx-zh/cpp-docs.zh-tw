---
title: 建立標題控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CHeaderCtrl class [MFC], creating
- header controls [MFC], creating
ms.assetid: 7864d9d2-4a2c-4622-b58b-7b110a1e28d2
ms.openlocfilehash: 22739e5671fb0300011de84d976eff0ce26eaedb
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907591"
---
# <a name="creating-the-header-control"></a>建立標題控制項

標題控制項無法直接在對話方塊編輯器中使用（雖然您可以加入清單控制項，其中包括標題控制項）。

### <a name="to-put-a-header-control-in-a-dialog-box"></a>將標題控制項放在對話方塊中

1. 在您的對話方塊類別中，手動內嵌[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)類型的成員變數。

1. 在[OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)中，建立並設定的樣式`CHeaderCtrl`、定位它，然後顯示。

1. 將專案加入至標題控制項。

1. 使用[類別 Wizard](reference/mfc-class-wizard.md)來對應對話方塊類別中的處理常式函式，以取得您需要處理的任何標頭控制項通知訊息（請參閱將[訊息對應至](../mfc/reference/mapping-messages-to-functions.md)函式）。

### <a name="to-put-a-header-control-in-a-view-not-a-clistview"></a>將標題控制項放在視圖中（不是 CListView）

1. 在您的 view 類別中內嵌[CHeaderCtrl](../mfc/reference/cheaderctrl-class.md)物件。

1. [樣式]、[位置] 和 [顯示[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)成員函式中的標題控制項] 視窗。

1. 將專案加入至標題控制項。

1. 使用 [[類別] Wizard](reference/mfc-class-wizard.md) ，針對您需要處理的任何標頭控制項通知訊息，對應 view 類別中的處理常式函式（請參閱將[訊息對應至函數](../mfc/reference/mapping-messages-to-functions.md)）。

不論是哪一種情況，都是在建立 view 或 dialog 物件時建立內嵌控制項物件。 接著，您必須呼叫[CHeaderCtrl：： create](../mfc/reference/cheaderctrl-class.md#create)來建立控制項視窗。 若要定位控制項，請呼叫[CHeaderCtrl：： Layout](../mfc/reference/cheaderctrl-class.md#layout)來決定控制項的初始大小和位置，並[SetWindowPos](../mfc/reference/cwnd-class.md#setwindowpos)以設定您想要的位置。 然後新增專案，如[將專案新增至標題控制項](../mfc/adding-items-to-the-header-control.md)中所述。

如需詳細資訊，請參閱在 Windows SDK 中[建立標題控制項](/windows/win32/Controls/header-controls)。

## <a name="see-also"></a>另請參閱

[使用 CHeaderCtrl](../mfc/using-cheaderctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
