---
title: 建立 CToolBarCtrl 物件
ms.date: 11/04/2016
helpviewer_keywords:
- toolbar controls [MFC], creating
- CToolBarCtrl class [MFC], creating toolbars
ms.assetid: a4f6bf0c-0195-4dbf-a09e-aee503e19dc3
ms.openlocfilehash: 2627f9aaceeab7760e15b23435233e124c5ea6f0
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84618996"
---
# <a name="creating-a-ctoolbarctrl-object"></a>建立 CToolBarCtrl 物件

[CToolBarCtrl](reference/ctoolbarctrl-class.md)物件包含數個內部資料結構（按鈕影像點陣圖清單、按鈕標籤字串清單，以及 `TBBUTTON` 結構清單），其會將影像和/或字串與按鈕的位置、樣式、狀態及命令識別碼產生關聯。 這些資料結構的每個元素都是以零為基底的索引來參考。 在您可以使用 `CToolBarCtrl` 物件之前，您必須先設定這些資料結構。 如需資料結構的清單，請參閱 Windows SDK 中的[工具列控制項](controls-mfc.md)。 字串清單只能用於按鈕標籤;您無法從工具列抓取字串。

若要使用 `CToolBarCtrl` 物件，您通常會執行下列步驟：

### <a name="to-use-a-ctoolbarctrl-object"></a>使用 CToolBarCtrl 物件

1. 建立[CToolBarCtrl](reference/ctoolbarctrl-class.md)物件。

1. 呼叫[create](reference/ctoolbarctrl-class.md#create)以建立 Windows 工具列通用控制項，並將它附加至 `CToolBarCtrl` 物件。 如果您想要按鈕的點陣圖影像，請呼叫[AddBitmap](reference/ctoolbarctrl-class.md#addbitmap)，將按鈕點陣圖新增至工具列。 如果您想要按鈕的字串標籤，請呼叫[AddString](reference/ctoolbarctrl-class.md#addstring)和/或[AddStrings](reference/ctoolbarctrl-class.md#addstrings)，將字串新增至工具列。 呼叫 `AddString` 和/或之後 `AddStrings` ，您應該呼叫[AutoSize](reference/ctoolbarctrl-class.md#autosize) ，以便取得要顯示的字串。

1. 藉由呼叫[AddButtons](reference/ctoolbarctrl-class.md#addbuttons)，將按鈕結構新增至工具列。

1. 如果您想要工具提示，請在工具列的 [擁有者] 視窗中處理**TTN_NEEDTEXT**訊息，如[處理工具提示通知](handling-tool-tip-notifications.md)中所述。

1. 如果您想要讓使用者能夠自訂工具列，請在擁有者視窗中處理自訂通知訊息，如[處理自訂通知](handling-customization-notifications.md)中所述。

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](using-ctoolbarctrl.md)<br/>
[控制項](controls-mfc.md)
