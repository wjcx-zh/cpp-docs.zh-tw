---
title: 終結視窗物件
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 363ff2a4cee48b1660de87714d73c93e795017cd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488800"
---
# <a name="destroying-window-objects"></a>終結視窗物件

必須小心使用您自己的子視窗終結時使用者已完成與視窗的 c + + 視窗物件。 不會終結這些物件，如果您的應用程式將不會復原其記憶體。 幸運的是，架構會處理視窗解構為建立框架視窗、 檢視和對話方塊。 如果您建立其他的 windows 時，您必須負責破壞它們。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [視窗解構序列](../mfc/window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

- [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)

- [一般視窗建立順序](../mfc/general-window-creation-sequence.md)

- [終結框架視窗](../mfc/destroying-frame-windows.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)

