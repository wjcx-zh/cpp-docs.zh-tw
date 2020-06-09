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
ms.openlocfilehash: 2e0484698654cd14f22a92be76a80f71c0f9adf5
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621849"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd

如果您需要規避物件 `HWND` 關聯性，MFC 會提供另一個 `CWnd` 成員函式[Detach](reference/cwnd-class.md#detach)，這會中斷 c + + 視窗物件與 Windows 視窗的連接。 這可防止析構函式在物件終結時終結 Windows 視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立視窗](creating-windows.md)

- [視窗銷毀順序](window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另請參閱

[視窗物件](window-objects.md)
