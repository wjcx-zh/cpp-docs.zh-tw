---
title: 樹狀目錄控制項標籤編輯
ms.date: 11/04/2016
helpviewer_keywords:
- editing tree control labels
- CTreeCtrl class [MFC], editing labels
- label editing in CTreeCtrl class [MFC]
- tree controls [MFC], label editing
ms.assetid: 6cde2ac3-43ee-468f-bac2-cf1a228ad32d
ms.openlocfilehash: 4b53d2c8e5a26a4dc37dfd7ae0710748bcd27bf6
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70741226"
---
# <a name="tree-control-label-editing"></a>樹狀目錄控制項標籤編輯

使用者可以直接在具有**TVS_EDITLABELS**樣式的樹狀目錄控制項（[CTreeCtrl](../mfc/reference/ctreectrl-class.md)）中編輯專案的標籤。 按一下具有焦點的項目標籤，使用者就可以開始進行編輯。 應用程式會使用[EditLabel](../mfc/reference/ctreectrl-class.md#editlabel)成員函式開始編輯。 當編輯開始和取消或完成時，樹狀目錄控制項會傳送通知。 當編輯完成時，您可以視狀況負責更新項目的標籤。

開始編輯標籤時，樹狀目錄控制項會傳送[TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit)通知訊息。 藉由處理這個通知，您可以允許編輯某些標籤並防止編輯其他標籤。 傳回 0 表示允許編輯，傳回非零值表示無法編輯。

取消或完成標籤編輯時，樹狀目錄控制項會傳送[TVN_ENDLABELEDIT](/windows/win32/Controls/tvn-endlabeledit)通知訊息。 *LParam*參數是[NMTVDISPINFO](/windows/win32/api/commctrl/ns-commctrl-nmtvdispinfow)結構的位址。 **專案**成員是一個[TVITEM](/windows/win32/api/commctrl/ns-commctrl-tvitemw)結構，可識別專案並包含編輯過的文字。 在驗證編輯字串後，您可以視狀況負責更新項目的標籤。 如果取消編輯， `TV_ITEM`的 pszText 成員就是0。

在標籤編輯期間，通常會回應[TVN_BEGINLABELEDIT](/windows/win32/Controls/tvn-beginlabeledit)通知訊息，您可以使用[GetEditControl](../mfc/reference/ctreectrl-class.md#geteditcontrol)成員函式，取得用於編輯標籤的編輯控制項指標。 您可以呼叫編輯控制項的[SetLimitText](../mfc/reference/cedit-class.md#setlimittext)成員函式，限制使用者可以輸入或子類別化編輯控制項來攔截和捨棄無效字元的文字量。 不過，請注意，只有在傳送**TVN_BEGINLABELEDIT** *之後*，才會顯示編輯控制項。

## <a name="see-also"></a>另請參閱

[使用 CTreeCtrl](../mfc/using-ctreectrl.md)<br/>
[控制項](../mfc/controls-mfc.md)
