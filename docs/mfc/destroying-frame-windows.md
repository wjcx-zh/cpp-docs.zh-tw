---
title: 終結框架視窗
ms.date: 11/04/2016
f1_keywords:
- PostNcDestroy
helpviewer_keywords:
- Default method [MFC]
- DestroyWindow method [MFC]
- frame windows [MFC], destroying
- OnNcDestroy method, and frame windows
- document frame windows [MFC], destroying
- destroying frame windows
- MFC, frame windows
- windows [MFC], destroying
- OnClose method [MFC]
- PostNcDestroy method [MFC]
ms.assetid: 5affca77-1999-4507-a2b2-9aa226611b4b
ms.openlocfilehash: b64298bd2b0f14c30c824d78947a17628adec8b5
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/04/2019
ms.locfileid: "57258199"
---
# <a name="destroying-frame-windows"></a>終結框架視窗

MFC 架構會處理視窗解構，以及建立這些 framework 文件和檢視表相關聯的視窗。 如果您建立其他的 windows 時，您必須負責破壞它們。

在架構中，當使用者關閉框架視窗時，視窗的預設[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 當 Windows 視窗終結時呼叫之最後一個成員函式[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，它會執行某些清除工作，會呼叫[預設](../mfc/reference/cwnd-class.md#default)成員函式以執行 Windows 清除，最後再呼叫虛擬成員函式[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)實作`PostNcDestroy`刪除 c + + 視窗物件。 您應該永遠不會使用 c + +**刪除**框架視窗上的運算子。 請改用 `DestroyWindow`。

當主視窗關閉時，應用程式就會關閉。 如果那里修改過但未儲存的文件，架構會顯示訊息方塊，詢問是否應該儲存文件，並可確保必要時，會儲存適當的文件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](../mfc/using-frame-windows.md)
