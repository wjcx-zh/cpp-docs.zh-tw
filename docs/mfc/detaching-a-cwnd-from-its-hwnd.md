---
title: 中斷連結從 HWND CWnd |Microsoft 文件
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
ms.openlocfilehash: a776b4ff4799750c89a322379a063030db748eec
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="detaching-a-cwnd-from-its-hwnd"></a>從 HWND 中斷連結 CWnd
如果您需要避免物件-`HWND`關聯性，MFC 提供另一個`CWnd`成員函式，[卸離](../mfc/reference/cwnd-class.md#detach)，這與 Windows 視窗中斷連線的 c + + 視窗物件。 這可防止解構函式物件終結時終結 Windows 視窗。  
  
## <a name="what-do-you-want-to-know-more-about"></a>您要更多詳細資訊  
  
-   [建立視窗](../mfc/creating-windows.md)  
  
-   [視窗解構序列](../mfc/window-destruction-sequence.md)  
  
-   [配置和解除配置視窗記憶體](../mfc/allocating-and-deallocating-window-memory.md)  
  
## <a name="see-also"></a>另請參閱  
 [視窗物件](../mfc/window-objects.md)

