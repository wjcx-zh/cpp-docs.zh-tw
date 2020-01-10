---
title: 建立強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed0fe3b7ef8aeddea01f573bfe8e1c01a6b5b443
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685673"
---
# <a name="creating-modal-dialog-boxes"></a>建立強制回應對話方塊

若要建立強制回應對話方塊，請呼叫[CDialog](../mfc/reference/cdialog-class.md)中所宣告的兩個公用函式的其中一個。 接下來，呼叫對話方塊物件的[DoModal](../mfc/reference/cdialog-class.md#domodal)成員函式來顯示對話方塊，並管理其互動，直到使用者選擇 [確定] 或 [取消] 為止。 由 `DoModal` 進行的這個管理會讓對話方塊強制回應。 對於強制回應對話方塊，`DoModal` 會載入對話方塊資源。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
