---
title: 編譯器錯誤 C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 75138bf8b090b7770d5bee918790efc095d76627
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761838"
---
# <a name="compiler-error-c3749"></a>編譯器錯誤 C3749

' attribute '：自訂屬性不能用在函式內

自訂屬性不能在函式內使用。 如需自訂屬性的詳細資訊，請參閱主題[屬性](../../windows/attributes/attribute.md)。

## <a name="example"></a>範例

下列範例會產生 C3749：

```cpp
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
