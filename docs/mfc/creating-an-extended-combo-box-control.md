---
title: 建立擴充的下拉式方塊控制項
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: d1e81664403f45a0a35cd24ceea16e1425b03403
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50668763"
---
# <a name="creating-an-extended-combo-box-control"></a>建立擴充的下拉式方塊控制項

建立擴充的下拉式方塊控制項的方式取決於您是在使用對話方塊中的控制項或建立在非對話方塊視窗中。

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CComboBoxEx

1. 在對話方塊編輯器中，將擴充的下拉式方塊控制項加入您的對話方塊範本資源。 指定其控制項 ID.

1. 指定需要，使用 [屬性] 對話方塊中，擴充的下拉式方塊控制項的樣式。

1. 使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)若要加入成員變數的型別[CComboBoxEx](../mfc/reference/ccomboboxex-class.md)與控制項屬性。 您可以使用這個成員呼叫 `CComboBoxEx` 成員函式。

1. 使用 [屬性] 視窗來對應您要處理任何擴充的下拉式方塊控制項通知訊息的對話方塊類別中的處理常式函式 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。

1. 在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，將其他樣式`CComboBoxEx`物件。

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>若要在非對話方塊視窗使用 CComboBoxEx

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](../mfc/reference/ctabctrl-class.md#create)成員函式，可能是在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，可能是與父視窗的為早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate)處理常式函式。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](../mfc/using-ccomboboxex.md)<br/>
[控制項](../mfc/controls-mfc.md)

