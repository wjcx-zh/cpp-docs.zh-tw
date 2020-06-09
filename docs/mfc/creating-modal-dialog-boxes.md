---
title: 建立強制回應對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- modal dialog boxes [MFC], creating
- MFC dialog boxes [MFC], creating
- MFC dialog boxes [MFC], modal
ms.assetid: 26c7a68c-79f6-4862-a5a8-6024984644d2
ms.openlocfilehash: ed7cc94982a46e542a5174d4d46b8013cc84ffa4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622973"
---
# <a name="creating-modal-dialog-boxes"></a>建立強制回應對話方塊

若要建立強制回應對話方塊，請呼叫[CDialog](reference/cdialog-class.md)中所宣告的兩個公用函式的其中一個。 接下來，呼叫對話方塊物件的[DoModal](reference/cdialog-class.md#domodal)成員函式來顯示對話方塊，並管理其互動，直到使用者選擇 [確定] 或 [取消] 為止。 由 `DoModal` 進行的這個管理會讓對話方塊強制回應。 對於強制回應對話方塊，`DoModal` 會載入對話方塊資源。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
