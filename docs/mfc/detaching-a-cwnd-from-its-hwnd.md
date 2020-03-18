---
title: 從 HWND 中斷連結 CWnd
ms.date: 11/04/2016
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: f7a6f97ba9f1dd3a928a5450c1a899ce09a4ac5f
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79446954"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd

如果您需要規避物件`HWND` 關聯性，MFC 會提供另一個 `CWnd` 的成員函式，卸[離](../mfc/reference/cwnd-class.md#detach)， C++這會中斷視窗物件與 Windows 視窗的連接。 這可防止析構函式在物件終結時終結 Windows 視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立視窗](../mfc/creating-windows.md)

- [視窗銷毀順序](../mfc/window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)
