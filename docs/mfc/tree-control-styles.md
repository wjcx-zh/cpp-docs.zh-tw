---
title: 樹狀目錄控制項樣式
ms.date: 11/04/2016
f1_keywords:
- TVS_SINGLEEXPAND
- TVS_LINESATROOT
- TVS_HASBUTTONS
- TVS_NOTOOLTIPS
- TVS_HASLINES
helpviewer_keywords:
- TVS_LINESATROOT [MFC]
- styles [MFC], CTreeCtrl
- styles [MFC], tree control
- TVS_HASLINES
- TVS_SINGLEEXPAND
- CTreeCtrl class [MFC], styles
- TVS_EDITLABELS [MFC]
- TVS_NOTOOLTIPS [MFC]
- TVS_HASBUTTONS [MFC]
- tree controls [MFC], styles
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
ms.openlocfilehash: f5f28025d0349e9bcd95aba50d4110d304fed376
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510933"
---
# <a name="tree-control-styles"></a>樹狀目錄控制項樣式

樹狀目錄控制項 ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) 樣式負責控制樹狀結構控制面板的各個層面。 當您建立樹狀目錄控制項時, 您可以設定初始樣式。 您可以使用[GetWindowLong](/windows/win32/api/winuser/nf-winuser-getwindowlongw)和[SetWindowLong](/windows/win32/api/winuser/nf-winuser-setwindowlongw) Windows 函式, 指定*nIndex*參數的**GWL_STYLE** , 在建立樹狀目錄控制項之後, 抓取和變更樣式。 如需樣式的完整清單, 請參閱 Windows SDK 中的[樹狀檢視控制項視窗樣式](/windows/win32/Controls/tree-view-control-window-styles)。

**TVS_HASLINES**樣式會藉由繪製將子專案連結至對應父專案的線條, 來增強樹狀結構控制項階層的圖形表示。 此樣式不會連結階層根目錄的專案。 若要這樣做, 您必須結合**TVS_HASLINES**和**TVS_LINESATROOT**樣式。

使用者可以按兩下父專案, 展開或折迭父項目的子專案清單。 具有**TVS_SINGLEEXPAND**樣式的樹狀目錄控制項, 會使選取的專案展開, 並取消選取要折迭的專案。 如果滑鼠是用來按一下選取的專案, 而該專案已關閉, 則會展開。 如果選取的專案在開啟時按下滑鼠, 則會折迭。

具有**TVS_HASBUTTONS**樣式的樹狀目錄控制項, 會在每個父項目的左側加入一個按鈕。 使用者可以按一下按鈕展開或折迭子專案, 做為按兩下父專案的替代方案。 **TVS_HASBUTTONS**不會將按鈕新增至階層根目錄的專案。 若要這樣做, 您必須結合**TVS_HASLINES**、 **TVS_LINESATROOT**和**TVS_HASBUTTONS**。

**TVS_EDITLABELS**樣式可以讓使用者編輯樹狀目錄控制項專案的標籤。 如需編輯標籤的詳細資訊, 請參閱本主題稍後的[樹狀目錄控制項標籤編輯](../mfc/tree-control-label-editing.md)。

**TVS_NOTOOLTIPS**樣式會停用樹狀檢視控制項的自動工具提示功能。 如果整個標題目前不可見, 此功能會自動顯示工具提示, 其中包含滑鼠游標下的專案標題。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
