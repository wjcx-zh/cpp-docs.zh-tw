---
title: 編譯器錯誤 C3749
ms.date: 11/04/2016
f1_keywords:
- C3749
helpviewer_keywords:
- C3749
ms.assetid: 3d26b468-4757-41b8-b5a2-78022a5295fb
ms.openlocfilehash: 7535f82a392f3d54b265ada2bd40a8d433838f4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227269"
---
# <a name="compiler-error-c3749"></a>編譯器錯誤 C3749

'attribute': 函式內可能未使用的自訂屬性

自訂屬性不能在函式。 如需有關自訂屬性的詳細資訊，請參閱主題[屬性](../../windows/attributes/attribute.md)。

## <a name="example"></a>範例

下列範例會產生 C3749:

```
// C3749a.cpp
// compile with: /clr /c
using namespace System;

[AttributeUsage(AttributeTargets::All)]
public ref struct ABC : public Attribute {
   ABC() {}
};

void f1() { [ABC]; };  // C3749
```
