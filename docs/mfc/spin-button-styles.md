---
title: 微調按鈕樣式
ms.date: 09/09/2019
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 1aae4b7e4c63929ebe03c97d50f05754bc13ec26
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907863"
---
# <a name="spin-button-styles"></a>微調按鈕樣式

微調按鈕（[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)）的許多設定都是由樣式所控制。 您可以使用 [[類別] Wizard](reference/mfc-class-wizard.md)來設定下列樣式。

- **方向**垂直或水準。 控制箭號按鈕的方向。 與 UDS_HORZ 樣式相關聯的。

- **對齊**其中一個未附加、左或右。 控制微調按鈕的位置。 在 [合作者] 視窗旁的 [微調] 按鈕的左邊和右邊位置。 好友視窗的寬度會減少，以配合微調按鈕。 與 UDS_ALIGNLEFT 和 UDS_ALIGNRIGHT 樣式相關聯。

- **自動好友**自動選取 [迭置順序] 中的上一個視窗，做為 [微調] 按鈕的合作者視窗。 在對話方塊範本中，這是定位順序中 [微調] 按鈕前面的控制項。 與 UDS_AUTOBUDDY 樣式相關聯的。

- **設定好友整數**當目前的位置變更時，讓微調控制項遞增和遞減好友視窗的標題。 與 UDS_SETBUDDYINT 樣式相關聯的。

- **無數以千計**不會在好友視窗標題的值中插入千位分隔符號。 與 UDS_NOTHOUSANDS 樣式相關聯的。

    > [!NOTE]
    >  如果您想要使用對話方塊資料交換（DDX）從「好友」控制項取得整數值，請設定此樣式。 `DDX_Text`不接受內嵌的千位分隔符號。

- **Wrap**使位置「換行」，因為該值會遞增或遞減超過控制項的範圍。 與 UDS_WRAP 樣式相關聯的。

- **方向鍵**當按下向上鍵和向下鍵時，讓微調按鈕遞增或遞減位置。 與 UDS_ARROWKEYS 樣式相關聯的。

## <a name="see-also"></a>另請參閱

[使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
