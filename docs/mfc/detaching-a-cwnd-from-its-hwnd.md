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
ms.openlocfilehash: fe4d9efa6adcec51d5944755e4a8abb1cc0784e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653969"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd

如果您要規避物件-`HWND`關聯性，MFC 提供另一個`CWnd`成員函式[卸離](../mfc/reference/cwnd-class.md#detach)，其中中斷 c + + 視窗物件 Windows 視窗中。 這可防止解構函式物件終結時終結 Windows 視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立視窗](../mfc/creating-windows.md)

- [視窗解構序列](../mfc/window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)

