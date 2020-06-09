---
title: 建立月曆控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CMonthCalCtrl class [MFC], creating
- month calendar controls [MFC], creating
- month calendar controls [MFC]
ms.assetid: 185cc642-85e9-4365-8a4c-d90b75b010f7
ms.openlocfilehash: 49d21bd4ce5aae23d5fc4c74567bc1c1d5a43570
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616228"
---
# <a name="creating-the-month-calendar-control"></a>建立月曆控制項

月曆控制項的建立方式，取決於您是在對話方塊中使用控制項，或在非對話方塊視窗建立控制項。

### <a name="to-use-cmonthcalctrl-directly-in-a-dialog-box"></a>直接在對話方塊使用 CMonthCalCtrl

1. 在對話方塊編輯器中，將月曆控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用月曆控制項的 [屬性] 對話方塊，指定需要的樣式。

1. 使用 [[加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md) ，以控制項屬性加入[CMonthCalCtrl](reference/cmonthcalctrl-class.md)類型的成員變數。 您可以使用這個成員呼叫 `CMonthCalCtrl` 成員函式。

1. 使用[類別 Wizard](reference/mfc-class-wizard.md)來對應對話方塊類別中的處理常式函式，以取得您需要處理的月曆控制項通知訊息（請參閱將[訊息對應至](reference/mapping-messages-to-functions.md)函式）。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，設定物件的任何其他樣式 `CMonthCalCtrl` 。

### <a name="to-use-cmonthcalctrl-in-a-nondialog-window"></a>在非對話方塊視窗使用 CMonthCalCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](reference/cmonthcalctrl-class.md#create)成員函式（可能是在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中），可能早于父視窗的[OnCreate](reference/cwnd-class.md#oncreate)處理函式（如果您要將控制項子類別化）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CMonthCalCtrl](using-cmonthcalctrl.md)<br/>
[控制項](controls-mfc.md)
