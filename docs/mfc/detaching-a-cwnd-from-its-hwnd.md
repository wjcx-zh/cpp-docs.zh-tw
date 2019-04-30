---
title: 從 HWND 中斷連結 CWnd
ms.date: 11/04/2016
f1_keywords:
- CWnd
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
ms.openlocfilehash: 259af94958f88643e9c3ce725b25c4e92cc38226
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394568"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd

如果您要規避物件-`HWND`關聯性，MFC 提供另一個`CWnd`成員函式[卸離](../mfc/reference/cwnd-class.md#detach)，其中斷連線C++從 Windows 視窗的視窗物件。 這可防止解構函式物件終結時終結 Windows 視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立視窗](../mfc/creating-windows.md)

- [視窗解構序列](../mfc/window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)
