---
title: 建立日期時間選擇器控制項
ms.date: 11/04/2016
helpviewer_keywords:
- DateTimePicker control [MFC], creating
- CDateTimeCtrl class [MFC], creating
ms.assetid: 764ec2fb-98cd-478b-a5f2-d63f0bb12279
ms.openlocfilehash: b3dd04d917667ff04001a455263d2a2f4af9bf9c
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282067"
---
# <a name="creating-the-date-and-time-picker-control"></a>建立日期時間選擇器控制項

建立日期和時間選擇器控制項的方式取決於您是在使用對話方塊中的控制項或建立在非對話方塊視窗中。

### <a name="to-use-cdatetimectrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CDateTimeCtrl

1. 在對話方塊編輯器中，將新增至您的對話方塊範本資源的日期和時間選擇器控制項。 指定其控制項 ID.

1. 指定需要，使用日期和時間選擇器控制項的 [屬性] 對話方塊中的任何樣式。

1. 使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)若要加入成員變數的型別[CDateTimeCtrl](../mfc/reference/cdatetimectrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CDateTimeCtrl` 成員函式。

1. 使用 [屬性] 視窗，將任何日期時間選擇器控制項的對話方塊類別中的處理常式函式對應[通知](../mfc/processing-notification-messages-in-date-and-time-picker-controls.md)您需要處理的訊息 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。

1. 在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，將其他樣式`CDateTimeCtrl`物件。

### <a name="to-use-cdatetimectrl-in-a-nondialog-window"></a>若要在非對話方塊視窗使用 CDateTimeCtrl

1. 宣告中的檢視或視窗類別的控制項。

1. 呼叫控制項的[Create](../mfc/reference/ctabctrl-class.md#create)成員函式，可能是在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，可能是與父視窗的為早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CDateTimeCtrl](../mfc/using-cdatetimectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
