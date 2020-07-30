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
ms.openlocfilehash: 33d471b41c8f1fd670e25626049ecd9b06b034e1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87195196"
---
# <a name="allocating-and-deallocating-window-memory"></a>配置和解除配置視窗記憶體

請勿使用 c + + **`delete`** 運算子來摧毀框架視窗或視圖。 相反地，呼叫 `CWnd` 成員函式 `DestroyWindow` 。 因此，您應該在堆積上使用運算子組態架構視窗 **`new`** 。 在堆疊框架上或全域組態架構視窗時，請務必小心。 其他視窗則應該盡可能在堆疊框架上配置。

## <a name="what-do-you-want-to-know-more-about"></a>您想要深入瞭解的內容

- [建立視窗](creating-windows.md)

- [視窗解構序列](window-destruction-sequence.md)

- [從 HWND 中斷連結 CWnd](detaching-a-cwnd-from-its-hwnd.md)

## <a name="see-also"></a>另請參閱

[終結視窗物件](destroying-window-objects.md)
