---
title: 在工具列控制項中使用下拉按鈕
ms.date: 11/04/2016
f1_keywords:
- TBN_DROPDOWN
- TBSTYLE_EX_DRAWDDARROWS
helpviewer_keywords:
- CToolBarCtrl class [MFC], drop-down buttons
- toolbars [MFC], drop-down buttons
- drop-down buttons in toolbars
- TBSTYLE_EX_DRAWDDARROWS
- TBN_DROPDOWN notification [MFC]
ms.assetid: b859f758-d2f6-40d9-9c26-0ff61993b9b2
ms.openlocfilehash: 0bc4df4c07ec4b8bc5b488925cbb140609302186
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365058"
---
# <a name="using-drop-down-buttons-in-a-toolbar-control"></a>在工具列控制項中使用下拉按鈕

除了標準按鈕外,工具列還可以具有下拉按鈕。 下拉按鈕通常由附加的下箭頭指示。

> [!NOTE]
> 僅當設置了TBSTYLE_EX_DRAWDDARROWS擴展樣式時,才會顯示附加的向下箭頭。

當用戶按下此箭頭(或按鈕本身,如果沒有箭頭),TBN_DROPDOWN通知消息發送到工具列控制件的父級。 然後,您可以處理此通知並顯示一個彈出式功能表;例如,您可以處理此通知並顯示一個彈出式功能表。類似於 Internet 資源管理員的行為。

以下過程展示如何使用彈出式選單實現下拉工具列按鈕:

### <a name="to-implement-a-drop-down-button"></a>實現下拉按鈕

1. 建立`CToolBarCtrl`物件後,請使用以下代碼設定TBSTYLE_EX_DRAWDDARROWS樣式:

   [!code-cpp[NVC_MFCControlLadenDialog#36](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_1.cpp)]

1. 設定任何新 ([插入按鈕](../mfc/reference/ctoolbarctrl-class.md#insertbutton)或[附加按鈕](../mfc/reference/ctoolbarctrl-class.md#addbuttons)) 或將成為下拉按鈕的現有[(SetButtonInfo)](../mfc/reference/ctoolbarctrl-class.md#setbuttoninfo)按鈕的TBSTYLE_DROPDOWN樣式。 以下範例展示修改`CToolBarCtrl`物件中的現有按鈕:

   [!code-cpp[NVC_MFCControlLadenDialog#37](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_2.cpp)]

1. 將TBN_DROPDOWN處理程式添加到工具列物件的父類。

   [!code-cpp[NVC_MFCControlLadenDialog#38](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_3.cpp)]

1. 在新處理程式中,顯示相應的彈出功能表。 以下代碼展示了一種方法:

   [!code-cpp[NVC_MFCControlLadenDialog#39](../mfc/codesnippet/cpp/using-drop-down-buttons-in-a-toolbar-control_4.cpp)]

## <a name="see-also"></a>另請參閱

[使用 CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
