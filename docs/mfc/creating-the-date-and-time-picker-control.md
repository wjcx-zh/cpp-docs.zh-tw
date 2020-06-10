---
title: 建立日期時間選擇器控制項
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: 5d753b166454b795932ec8f47b0897829fab9b8e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84620475"
---
# <a name="creating-the-date-and-time-picker-control"></a>建立日期時間選擇器控制項

建立日期和時間選擇器控制項的方式，取決於您是在對話方塊中使用控制項，還是在非對話方塊視窗中建立。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>直接在對話方塊中使用 CDateTimeCtrl

1. 在對話方塊編輯器中，將日期和時間選擇器控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用 [日期和時間選擇器] 控制項的 [屬性] 對話方塊，指定所需的任何樣式。

1. 使用 [[加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md) ，以控制項屬性加入[CDateTimeCtrl](reference/cdatetimectrl-class.md)類型的成員變數。 您可以使用這個成員呼叫 `CDateTimeCtrl` 成員函式。

1. 使用[類別 Wizard](reference/mfc-class-wizard.md)來對應對話方塊類別中的處理常式函式，以取得您需要處理的任何日期時間選擇器控制項[通知](processing-notification-messages-in-date-and-time-picker-controls.md)訊息（請參閱[將訊息對應至](reference/mapping-messages-to-functions.md)函式）。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，設定物件的任何其他樣式 `CDateTimeCtrl` 。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>在非對話方塊視窗中使用 CDateTimeCtrl

1. 在 view 或 window 類別中宣告控制項。

1. 呼叫控制項的[Create](reference/ctabctrl-class.md#create)成員函式（可能是在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中），可能早于父視窗的[OnCreate](reference/cwnd-class.md#oncreate)處理函式（如果您要將控制項子類別化）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](using-cdatetimectrl.md)<br/>
[控制項](controls-mfc.md)
