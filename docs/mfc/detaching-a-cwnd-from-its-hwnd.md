---
title: 中斷連結 CWnd 從 HWND |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- CWnd
dev_langs:
- C++
helpviewer_keywords:
- HWND, detaching CWnd from
- removing HWNDs from CWnds
- CWnd objects [MFC], detaching from HWND
- detaching CWnds from HWNDs
- Detach method (CWnd class)
ms.assetid: 6efadf84-0517-4a3f-acfd-216e088f19c6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c69703d8c528d82a696fc94be76ac4a569628b4e
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46392641"
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd

如果您要規避物件-`HWND`關聯性，MFC 提供另一個`CWnd`成員函式[卸離](../mfc/reference/cwnd-class.md#detach)，其中中斷 c + + 視窗物件 Windows 視窗中。 這可防止解構函式物件終結時終結 Windows 視窗。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立視窗](../mfc/creating-windows.md)

- [視窗解構序列](../mfc/window-destruction-sequence.md)

- [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)

## <a name="see-also"></a>另請參閱

[視窗物件](../mfc/window-objects.md)

