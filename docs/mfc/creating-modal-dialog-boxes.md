---
title: 建立強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: eb9aab7e8579fbbbfdf5d0f2dca9b6e6abea0066
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657329"
---
# <a name="creating-modal-dialog-boxes"></a>建立強制回應對話方塊

若要建立強制回應對話方塊中，呼叫兩個公用建構函式中宣告[CDialog](../mfc/reference/cdialog-class.md)。 接下來，呼叫對話方塊物件的[DoModal](../mfc/reference/cdialog-class.md#domodal)成員函式來顯示對話方塊和管理與其互動，直到使用者選擇 [確定] 或 [取消]。 由 `DoModal` 進行的這個管理會讓對話方塊強制回應。 對於強制回應對話方塊，`DoModal` 會載入對話方塊資源。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

