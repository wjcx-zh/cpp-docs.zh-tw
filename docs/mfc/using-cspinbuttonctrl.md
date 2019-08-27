---
title: 使用 CSpinButtonCtrl
ms.date: 11/04/2016
f1_keywords:
- CSpinButtonCtrl
helpviewer_keywords:
- up-down controls [MFC], spin button control
- up-down controls
- spin button control
- CSpinButtonCtrl class [MFC], using
ms.assetid: a91db36b-e11e-42ef-8e89-51915cc486d2
ms.openlocfilehash: a2a12672f0e70248e135bdd177b76589b6197c75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513474"
---
# <a name="using-cspinbuttonctrl"></a>使用 CSpinButtonCtrl

*微調按鈕*控制項 (也稱為*上下*按鈕控制項) 提供一對箭號, 讓使用者可以按一下來調整值。 這個值就是所謂的*目前位置*。 此位置會保持在微調按鈕的範圍內。 當使用者按一下向上箭號時，此位置會朝最大值移動，當使用者按一下向下箭號時，此位置會朝最小值移動。

微調按鈕控制項會在 MFC 中以[CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)類別表示。

> [!NOTE]
>  根據預設，微調按鈕的範圍具有最大值為零 (0) 和最小值為 100。 因為最大值小於最小值，因此按一下向上箭號會遞減位置，按一下向下箭號會遞增位置。 請使用[CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)來調整這些值。

通常，目前位置會顯示於附屬控制項中。 隨附的控制項稱為「*合作者視窗*」。 如需微調按鈕控制項的圖例, 請參閱[關於](/windows/win32/Controls/up-down-controls)Windows SDK 中的上下調整控制項。

在 Visual Studio 中，若要建立一個微調控制項以及一個編輯控制項協同視窗，請先將編輯控制項加入至對話方塊或視窗，然後再拖曳微調控制項。 選取微調控制項並設定其 [**自動好友**], 並**將 [好友整數**] 屬性設為 [ **True**]。 同時設定**對齊**屬性;最常見的是靠**右對齊**。 這些設定將編輯控制項設定為協同視窗，因為它的定位順序直接位在編輯控制項之前。 編輯控制項會顯示整數，而微調控制項會內嵌在編輯控制項的右邊。 (選擇性) 您可以使用[CSpinButtonCtrl:: SetRange](../mfc/reference/cspinbuttonctrl-class.md#setrange)方法來設定微調控制項的有效範圍。 微調控制項和協同視窗之間不需要透過事件處理常式進行溝通，它們會直接交換資料。 如果您將微調控制項用於其他用途, 例如, 若要逐頁流覽一系列視窗或對話方塊, 請新增 UDN_DELTAPOS 訊息的處理常式, 並在該處執行自訂動作。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [微調按鈕樣式](../mfc/spin-button-styles.md)

- [微調按鈕成員函式](../mfc/spin-button-member-functions.md)

## <a name="see-also"></a>另請參閱

[控制項](../mfc/controls-mfc.md)
