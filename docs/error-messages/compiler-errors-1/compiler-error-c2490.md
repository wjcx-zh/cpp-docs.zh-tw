---
title: 編譯器錯誤 C2490
ms.date: 11/04/2016
f1_keywords:
- C2490
helpviewer_keywords:
- C2490
ms.assetid: 9de6bddd-b2e2-4ce6-b33b-201a8c2c8c54
ms.openlocfilehash: 9e06883d0e8b6103eb44d086d3872d86c50a58b6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361800"
---
# <a name="compiler-error-c2490"></a>編譯器錯誤 C2490

具有 'naked' 屬性的函式中不允許 ' keyword'

做為定義的函式[naked](../../cpp/naked-cpp.md)無法使用結構化例外狀況處理。

下列範例會產生 C2490:

```
// C2490.cpp
// processor: x86
__declspec( naked ) int func() {
   __try{}   // C2490, structured exception handling
}
```