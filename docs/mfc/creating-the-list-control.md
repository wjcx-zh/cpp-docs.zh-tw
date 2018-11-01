---
title: 建立清單控制項
ms.date: 11/04/2016
helpviewer_keywords:
- CListCtrl class [MFC], creating control
- list controls [MFC]
ms.assetid: a4cb1729-31b6-4d2b-a44b-367474848a39
ms.openlocfilehash: b21fb8a7721df571dbe4d65c28053af3610d9bf7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50495251"
---
# <a name="creating-the-list-control"></a>建立清單控制項

如何控制清單 ([CListCtrl](../mfc/reference/clistctrl-class.md)) 建立取決於您是直接使用控制項還是使用類別[CListView](../mfc/reference/clistview-class.md)改。 如果您使用`CListView`，framework 建構檢視做為其文件/檢視建立順序的一部分。 建立清單檢視會建立清單控制項也 （兩個是相同的東西）。 在檢視中建立控制項[OnCreate](../mfc/reference/cwnd-class.md#oncreate)處理常式函式。 在此情況下，控制項可讓您將新增項目，透過呼叫[GetListCtrl](../mfc/reference/clistview-class.md#getlistctrl)。

### <a name="to-use-clistctrl-directly-in-a-dialog-box"></a>在對話方塊中直接使用 CListCtrl

1. 在對話方塊編輯器中，加入您的對話方塊範本資源中的清單控制項。 指定其控制項 ID.

1. 使用[加入成員變數精靈](../ide/adding-a-member-variable-visual-cpp.md)若要加入成員變數的型別`CListCtrl`與控制項屬性。 您可以使用這個成員呼叫 `CListCtrl` 成員函式。

1. 使用 [屬性] 視窗來對應對話方塊類別中的處理常式函式的任何清單控制項通知訊息，您需要將處理 (請參閱[將訊息對應至函式](../mfc/reference/mapping-messages-to-functions.md))。

1. 在  [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog)，設定樣式的`CListCtrl`。 請參閱[變更清單控制項樣式](../mfc/changing-list-control-styles.md)。 雖然您可以稍後變更檢視，這會決定在控制項中，您收到 「 檢視 」 的類型。

### <a name="to-use-clistctrl-in-a-nondialog-window"></a>若要在非對話方塊視窗使用 CListCtrl

1. 在檢視或視窗類別中定義控制項。

1. 呼叫控制項的[Create](../mfc/reference/clistctrl-class.md#create)成員函式，可能是在[OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate)，可能是與父視窗的為早期[OnCreate](../mfc/reference/cwnd-class.md#oncreate) （如果您目前的處理常式函式子類別化控制項）。 設定控制項的樣式。

## <a name="see-also"></a>另請參閱

[使用 CListCtrl](../mfc/using-clistctrl.md)<br/>
[控制項](../mfc/controls-mfc.md)

