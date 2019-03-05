---
title: 建立月曆控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 809bc9fdf6b4477363d0a43d007a2884bb43a049
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258745"
---
# <a name="creating-the-month-calendar-control"></a>建立月曆控制項

月曆控制項的建立方式，取決於您是在對話方塊中使用控制項，或在非對話方塊視窗建立控制項。

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>直接在對話方塊使用 CMonthCalCtrl

1. 在對話方塊編輯器中，將月曆控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用月曆控制項的 [屬性] 對話方塊，指定需要的樣式。

1. 使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)若要加入成員變數的型別[CMonthCalCtrl](../mfc/reference/cmonthcalctrl-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CMonthCalCtrl` 成員函式。

1. 使用 [屬性] 視窗的任何月曆控制項告知訊息對應對話方塊類別中的處理常式函式需要將處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。

1. 在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，將其他樣式`CMonthCalCtrl`物件。

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>在非對話方塊視窗使用 CMonthCalCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](../mfc/reference/cmonthcalctrl-class.md#create)成員函式，可能是在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，可能是與父視窗的為早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](../mfc/using-cmonthcalctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
