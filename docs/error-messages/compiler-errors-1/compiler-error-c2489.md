---
title: 編譯器錯誤 C2489
ms.date: 11/04/2016
f1_keywords:
- C2489
helpviewer_keywords:
- C2489
ms.assetid: 67d8cd98-db7e-4f7f-86b4-4af7bc89ec8b
ms.openlocfilehash: e4024455e17956fc67917e92a3ca531eca5c5e04
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62361031"
---
# <a name="compiler-error-c2489"></a>編譯器錯誤 C2489

'identifier': 'naked' 函式中不允許在函式範圍的自動或暫存器變數的初始化

如需詳細資訊，請參閱 < [naked](../../cpp/naked-cpp.md)。

下列範例會產生 C2489:

```
// C2489.cpp
// processor: x86
__declspec( naked ) int func() {
   int i = 1;   // C2489
   register int j = 1;   // C2489
}
```