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
ms.openlocfilehash: 8b407c6e832dde7a5865146e7cc12d1840d3234a
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/30/2019
ms.locfileid: "71685861"
---
# <a name="destroying-the-dialog-box"></a>終結對話方塊

強制回應對話方塊通常會在堆疊框架上建立，並在建立它們的函式結束時終結。 當物件超出範圍時，會呼叫對話方塊物件的析構函式。

非強制回應對話方塊通常是由父視圖或框架視窗（應用程式的主框架視窗或檔框架視窗）所建立和擁有。 預設的[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)，這會破壞對話方塊視窗。 如果對話方塊單獨出現，而且沒有指向它的指標或其他特殊擁有權的語義，您應該覆寫[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)以C++終結對話方塊物件。 您也應該覆寫[OnCancel](../mfc/reference/cdialog-class.md#oncancel) ，並從它內呼叫 `DestroyWindow`。 如果沒有，對話方塊的擁有者應該會在不再需要C++時終結物件。

## <a name="see-also"></a>另請參閱

[在 MFC 中使用對話方塊](../mfc/life-cycle-of-a-dialog-box.md)
