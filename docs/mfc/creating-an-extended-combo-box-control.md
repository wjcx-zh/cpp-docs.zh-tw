---
title: 建立擴充的下拉式方塊控制項
ms.date: 11/04/2016
helpviewer_keywords:
- extended combo boxes
- CComboBoxEx class [MFC], creating extended combo box controls
- extended combo boxes [MFC], creating
ms.assetid: a964267e-97b6-4e77-9f89-55bb5c68913f
ms.openlocfilehash: 554085304f5330ac9cd99a5b814af26ce3a9c7e6
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84616289"
---
# <a name="creating-an-extended-combo-box-control"></a>建立擴充的下拉式方塊控制項

擴充下拉式方塊控制項的建立方式，取決於您是在對話方塊中使用控制項，還是在非對話方塊視窗中建立。

### <a name="to-use-ccomboboxex-directly-in-a-dialog-box"></a>直接在對話方塊中使用 CComboBoxEx

1. 在對話方塊編輯器中，將擴充的下拉式方塊控制項加入至對話方塊範本資源。 指定其控制項 ID.

1. 使用擴充下拉式方塊控制項的 [屬性] 對話方塊，指定所需的任何樣式。

1. 使用 [[加入成員變數] Wizard](../ide/adding-a-member-variable-visual-cpp.md) ，以控制項屬性加入[CComboBoxEx](reference/ccomboboxex-class.md)類型的成員變數。 您可以使用這個成員呼叫 `CComboBoxEx` 成員函式。

1. 使用 [[類別] [Wizard]](reference/mfc-class-wizard.md) ，針對您需要處理的任何擴充下拉式方塊控制項通知訊息，對應對話方塊類別中的處理常式函式（請參閱將[訊息對應至](reference/mapping-messages-to-functions.md)函式）。

1. 在[OnInitDialog](reference/cdialog-class.md#oninitdialog)中，設定物件的任何其他樣式 `CComboBoxEx` 。

### <a name="to-use-ccomboboxex-in-a-nondialog-window"></a>在非對話方塊視窗中使用 CComboBoxEx

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](reference/ctabctrl-class.md#create)成員函式（可能是在[OnInitialUpdate](reference/cview-class.md#oninitialupdate)中），可能早于父視窗的[OnCreate](reference/cwnd-class.md#oncreate)處理函式。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CComboBoxEx](using-ccomboboxex.md)<br/>
[控制項](controls-mfc.md)
