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
ms.openlocfilehash: 02546559183d0e14973bc2e5ccb26a4570a39b1e
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84623258"
---
# <a name="allocating-and-deallocating-window-memory"></a>配置和解除配置視窗記憶體

請勿使用 c + + **delete**運算子來摧毀框架視窗或視圖。 相反地，呼叫 `CWnd` 成員函式 `DestroyWindow` 。 因此，框架視窗應該在具有 operator **new**的堆積上配置。 在堆疊框架上或全域組態架構視窗時，請務必小心。 其他視窗則應該盡可能在堆疊框架上配置。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立視窗](creating-windows.md)

- [視窗銷毀順序](window-destruction-sequence.md)

- [從 HWND 卸離 CWnd](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>另請參閱

[終結視窗物件](destroying-window-objects.md)
