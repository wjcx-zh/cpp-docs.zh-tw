---
title: 編譯器錯誤 C2490
ms.date: 11/04/2016
f1_keywords:
- C2490
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
ms.openlocfilehash: 86d9f41db8ba386a64878eebfae989011f637d71
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757081"
---
# <a name="compiler-error-c2490"></a>編譯器錯誤 C2490

' naked ' 屬性的函式中不允許 ' 關鍵字 '

定義為[naked](../../cpp/naked-cpp.md)的函數不能使用結構化例外狀況處理。

下列範例會產生 C2490：

```cpp
// C2490.cpp
// processor: x86
__declspec( naked ) int func() {
   __try{}   // C2490, structured exception handling
}
```
