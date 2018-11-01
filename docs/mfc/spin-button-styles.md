---
title: 微調按鈕樣式
ms.date: 11/04/2016
helpviewer_keywords:
- styles [MFC], CSpinButtonCtrl
- CSpinButtonCtrl class [MFC], styles
- styles [MFC], spin button control
- spin button control, styles
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
ms.openlocfilehash: 73042dbbdc28819ecc736c282599189ee074ce77
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50457105"
---
# <a name="spin-button-styles"></a>微調按鈕樣式

許多微調按鈕的設定 ([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)) 所控制的樣式。 您可以設定使用下列樣式**屬性**在對話方塊編輯器 視窗。

- **方向**垂直或水平。 控制方向的箭號按鈕。 相關聯的 UDS_HORZ 樣式。

- **對齊**其中未連結、 左邊或右邊。 控制微調按鈕的位置。 左邊和右邊位置微調按鈕旁邊協同視窗。 協同視窗的寬度會縮小以容納微調按鈕。 相關聯的 UDS_ALIGNLEFT 和 UDS_ALIGNRIGHT 樣式。

- **Auto Buddy**作為微調按鈕的協同視窗會自動選取疊置順序的上一個視窗。 在對話方塊範本中，這是之前的定位順序中的微調按鈕控制項。 相關聯的 UDS_AUTOBUDDY 樣式。

- **設定 Buddy Integer**使遞增和遞減目前的位置變更的協同視窗之標題的微調控制項。 相關聯的 UDS_SETBUDDYINT 樣式。

- **No Thousands**不插入千位分隔符號的協同視窗標題中的值。 相關聯的 UDS_NOTHOUSANDS 樣式。

    > [!NOTE]
    >  如果您想要使用對話方塊資料交換 (DDX) 若要發揮協同控制項的整數值，請設定此樣式。 `DDX_Text` 不接受內嵌的千位分隔符號。

- **包裝**會導致 「 包裝 」，此值會遞增或遞減的控制項範圍以外的位置。 相關聯的 UDS_WRAP 樣式。

- **方向鍵**會導致遞增或遞減位置，按下向上鍵和向下鍵會微調按鈕。 相關聯的 UDS_ARROWKEYS 樣式。

## <a name="see-also"></a>另請參閱

[使用 CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

