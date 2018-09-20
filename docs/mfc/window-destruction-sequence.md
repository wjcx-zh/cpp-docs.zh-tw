---
title: 視窗解構序列 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- destruction, windows
- destroying windows
- sequence [MFC], window destruction
- CWnd objects [MFC], destruction sequence
- sequence [MFC]
- windows [MFC], destroying
ms.assetid: 2d819196-6240-415f-a308-db43745e616c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 04ef1aa9dadbbe965ab17945da681a0e1189c404
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446634"
---
# <a name="window-destruction-sequence"></a>視窗解構序列

在 MFC 架構中，當使用者關閉框架視窗時，視窗的預設[OnClose](../mfc/reference/cwnd-class.md#onclose)處理常式會呼叫[DestroyWindow](../mfc/reference/cwnd-class.md#destroywindow)。 當 Windows 視窗終結時呼叫之最後一個成員函式[OnNcDestroy](../mfc/reference/cwnd-class.md#onncdestroy)，它會執行某些清除工作，會呼叫[預設](../mfc/reference/cwnd-class.md#default)成員函式以執行 Windows 清除，最後再呼叫虛擬成員函式[PostNcDestroy](../mfc/reference/cwnd-class.md#postncdestroy)。 [CFrameWnd](../mfc/reference/cframewnd-class.md)實作`PostNcDestroy`刪除 c + + 視窗物件。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

- [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>另請參閱

[終結視窗物件](../mfc/destroying-window-objects.md)

