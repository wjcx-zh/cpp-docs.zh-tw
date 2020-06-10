---
title: 建立清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: c9ba379611c44b5eae8d02b908ba71e3dbd66481
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617102"
---
# <a name="creating-the-list-control"></a>建立清單控制項

建立清單控制項（[CListCtrl](reference/clistctrl-class.md)）的方式，取決於您是直接使用控制項，還是改為使用類別[CListView](reference/clistview-class.md) 。 如果您使用 `CListView` ，架構會將此視圖視為其檔/視圖建立順序的一部分。 建立清單視圖也會建立清單控制項（兩者的內容相同）。 控制項會在 view 的[OnCreate](reference/cwnd-class.md#oncreate) handler 函數中建立。 在此情況下，控制項已準備好讓您透過呼叫[GetListCtrl](reference/clistview-class.md#getlistctrl)來加入專案。

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>直接在對話方塊中使用 CListCtrl

1. 在對話方塊編輯器中，將清單控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用 [[加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md)來加入 `CListCtrl` 具有控制項屬性之類型的成員變數。 您可以使用這個成員呼叫 `CListCtrl` 成員函式。

1. 使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，針對您需要處理的任何清單控制項通知訊息，對應對話方塊類別中的處理常式函式（請參閱將[訊息對應至](reference/mapping-messages-to-functions.md)函式）。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，設定的樣式 `CListCtrl` 。 請參閱[變更清單控制項樣式](changing-list-control-styles.md)。 這會決定您在控制項中取得的「view」類型，雖然您可以在稍後變更此視圖。

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>在非對話方塊視窗中使用 CListCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](reference/clistctrl-class.md#create)成員函式（可能是在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中），可能早于父視窗的[OnCreate](reference/cwnd-class.md#oncreate)處理函式（如果您要將控制項子類別化）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](using-clistctrl.md)<br/>
[控制項](controls-mfc.md)
