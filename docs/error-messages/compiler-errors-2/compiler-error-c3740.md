---
title: 編譯器錯誤 C3740
ms.date: 11/04/2016
f1_keywords:
- C3740
helpviewer_keywords:
- C3740
ms.assetid: edb17a90-2307-4df6-943d-580460d26d2b
ms.openlocfilehash: 4e32c37853f4c877e6260e38daa0c8357ca54a25
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74752661"
---
# <a name="compiler-error-c3740"></a>編譯器錯誤 C3740

範本不能來源或接收事件

樣板化類別或結構不能包含[事件](../../cpp/event-handling.md)。

下列範例會產生 C3740：

```cpp
// C3740.cpp
template <typename T>   // Delete the template specification
struct E {
   __event void f();   // C3740
};

int main() {
}
```
