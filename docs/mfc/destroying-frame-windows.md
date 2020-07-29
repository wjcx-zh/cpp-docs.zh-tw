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
ms.openlocfilehash: 20eefa2be6d0e0df4585834bae5c37cd258610a7
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87214135"
---
# <a name="destroying-frame-windows"></a>終結框架視窗

MFC 架構會管理視窗的銷毀，以及與架構檔和視圖相關聯之視窗的建立。 如果您建立其他視窗，您必須負責終結它們。

在架構中，當使用者關閉框架視窗時，視窗的預設[OnClose](reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](reference/cwnd-class.md#destroywindow)。 當 Windows 視窗終結時所呼叫的最後一個成員函式是[OnNcDestroy](reference/cwnd-class.md#onncdestroy)，它會進行一些清除，呼叫[預設](reference/cwnd-class.md#default)成員函式來執行 Windows 清除，最後再呼叫虛擬成員函式[PostNcDestroy](reference/cwnd-class.md#postncdestroy)。 的[CFrameWnd](reference/cframewnd-class.md)執行會 `PostNcDestroy` 刪除 c + + 視窗物件。 您絕對不應該在框架視窗上使用 c + + **`delete`** 運算子。 請改用 `DestroyWindow`。

主視窗關閉時，應用程式會關閉。 如果有已修改的未儲存檔，此架構會顯示訊息方塊，詢問是否應儲存檔，並確保在必要時儲存適當的檔。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立文件框架視窗](creating-document-frame-windows.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](using-frame-windows.md)
