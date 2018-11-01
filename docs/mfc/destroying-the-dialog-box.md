---
title: 終結對話方塊
ms.date: 11/04/2016
helpviewer_keywords:
- dialog boxes [MFC], deleting
- destruction, dialog box
- dialog boxes [MFC], destroying
- dialog boxes [MFC], removing
- modeless dialog boxes [MFC], destroying
- MFC dialog boxes [MFC], destroying
- modal dialog boxes [MFC], destroying
ms.assetid: dabceee7-3639-4d85-bf34-73515441b3d0
ms.openlocfilehash: f84e36a2a002610c294653012c40707fddcaba54
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50607463"
---
# <a name="destroying-the-dialog-box"></a>終結對話方塊

強制回應對話方塊通常堆疊框架上建立和終結建立它們的函式結束時。 當物件超出範圍時，會呼叫對話方塊物件的解構函式。

非強制回應對話方塊通常建立並由父檢視或框架視窗擁有 — 應用程式的主框架視窗或文件框架視窗。 預設值[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，即已遭終結對話方塊視窗。 如果對話方塊中都是獨立的與任何指標，或其他特殊的擁有權語意的您應該覆寫[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)終結 c + + 對話方塊物件。 您也應該覆寫[OnCancel](../mfc/reference/cdialog-class.md#oncancel) ，並呼叫`DestroyWindow`從在其中。 如果沒有，不再需要時，對話方塊中的擁有者應該終結 c + + 物件。

## <a name="see-also"></a>另請參閱

[對話方塊的生命週期](../mfc/life-cycle-of-a-dialog-box.md)

