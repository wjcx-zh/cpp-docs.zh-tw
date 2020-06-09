---
title: 終結視窗物件
ms.date: 11/04/2016
helpviewer_keywords:
- frame windows [MFC], destroying
- window objects [MFC], deleting
- window objects [MFC], destroying
- window objects [MFC], removing
ms.assetid: 3241fea0-c614-4a25-957d-20f21bd5fd0c
ms.openlocfilehash: 22b483c1005931b229453ae229935c0e716ab726
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621855"
---
# <a name="destroying-window-objects"></a>終結視窗物件

當使用者完成視窗時，必須小心使用您自己的子視窗來摧毀 c + + 視窗物件。 如果未終結這些物件，您的應用程式將無法復原其記憶體。 幸好，此架構會管理視窗銷毀，以及框架視窗、視圖和對話方塊的建立。 如果您建立其他視窗，您必須負責終結它們。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [視窗銷毀順序](window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](allocating-and-deallocating-window-memory.md)

- [從 HWND 卸離 CWnd](detaching-a-cwnd-from-its-hwnd.md)

- [一般視窗建立順序](general-window-creation-sequence.md)

- [終結框架視窗](destroying-frame-windows.md)

## <a name="see-also"></a>另請參閱

[視窗物件](window-objects.md)
