---
title: 初始化 CWnd 物件的時機
ms.date: 11/04/2016
helpviewer_keywords:
- window objects [MFC], when to initialize CWnd
- initializing CWnd objects [MFC]
- initializing objects [MFC], CWnd
- CWnd objects [MFC], when HWND is attached
- HWND, when attached to CWnd object
- CWnd objects [MFC], when to initialize
ms.assetid: 4d31bcb1-73db-4f2f-b71c-89b087569a10
ms.openlocfilehash: c75745547846fbf6c7e01ecf473d4d6f366bd264
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548547"
---
# <a name="when-to-initialize-cwnd-objects"></a>初始化 CWnd 物件的時機

您無法建立您自己的子視窗或呼叫 Windows API 中的任何函式中的建構函式`CWnd`-衍生物件。 這是因為`HWND`針對`CWnd`物件尚未建立。 中，必須完成最 Windows 特定的初始化，例如新增子視窗[OnCreate](../mfc/reference/cwnd-class.md#oncreate)訊息處理常式。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立文件框架視窗](../mfc/creating-document-frame-windows.md)

- [文件/檢視建立](../mfc/document-view-creation.md)

## <a name="see-also"></a>另請參閱

[使用框架視窗](../mfc/using-frame-windows.md)

