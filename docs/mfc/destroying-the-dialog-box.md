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
ms.openlocfilehash: 9b1244b03dc3f6f418730dd782050448f3bf8934
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621908"
---
# <a name="destroying-the-dialog-box"></a>終結對話方塊

強制回應對話方塊通常會在堆疊框架上建立，並在建立它們的函式結束時終結。 當物件超出範圍時，會呼叫對話方塊物件的析構函式。

非強制回應對話方塊通常是由父視圖或框架視窗（應用程式的主框架視窗或檔框架視窗）所建立和擁有。 預設的[OnClose](reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](reference/cwnd-class.md#destroywindow)，這會破壞對話方塊視窗。 如果對話方塊單獨出現，而且沒有指向它的指標或其他特殊擁有權的語義，您應該覆寫[PostNcDestroy](reference/cwnd-class.md#postncdestroy)以終結 c + + 對話方塊物件。 您也應該覆寫[OnCancel](reference/cdialog-class.md#oncancel) ，並 `DestroyWindow` 從它內呼叫。 如果沒有，對話方塊的擁有者應該會在不再需要 c + + 物件時予以終結。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](life-cycle-of-a-dialog-box.md)
