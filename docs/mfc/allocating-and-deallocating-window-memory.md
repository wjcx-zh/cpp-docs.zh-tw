---
title: 配置和解除配置視窗記憶體
ms.date: 11/04/2016
helpviewer_keywords:
- memory allocation, window objects
- memory deallocation
- storage for window objects [MFC]
- memory deallocation, window memory
- window objects [MFC], deallocating memory for
- storage for window objects [MFC], allocating
ms.assetid: 7c962539-8461-4846-b5ca-fe3b15c313dc
ms.openlocfilehash: 60f99c01c7a311c31602269b49efaf434d16827a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62394698"
---
# <a name="allocating-and-deallocating-window-memory"></a>配置和解除配置視窗記憶體

請勿使用C++**刪除**終結框架視窗或檢視表的運算子。 請改為呼叫`CWnd`成員函式`DestroyWindow`。 框架視窗，因此，應該會在堆積上配置與運算子**新**。 配置框架視窗的堆疊框架或全域時要小心。 其他視窗應該盡可能的堆疊框架上配置。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入了解什麼

- [建立視窗](../mfc/creating-windows.md)

- [視窗解構序列](../mfc/window-destruction-sequence.md)

- [中斷連結從 HWND CWnd](../mfc/detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>另請參閱

[終結視窗物件](../mfc/destroying-window-objects.md)
