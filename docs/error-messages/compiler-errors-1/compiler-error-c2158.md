---
title: 編譯器錯誤 C2158
ms.date: 11/04/2016
f1_keywords:
- C2158
helpviewer_keywords:
- C2158
ms.assetid: 39028899-e95c-4809-8e65-6111118641ee
ms.openlocfilehash: f098af90d3052d6961eb0892085c02f2e42bbed4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755851"
---
# <a name="compiler-error-c2158"></a>編譯器錯誤 C2158

'type': #pragma make_public 指示詞目前僅支援原生非樣板類型

[make_public](../../preprocessor/make-public.md) pragma 只能套用至原生非樣板類型。

## <a name="example"></a>範例

下列範例會產生 C2158。

```cpp
// C2158.cpp
// compile with: /clr /c
ref class A {};
#pragma make_public(A)   // C2158

template< typename T >
class B {};
#pragma make_public(B)   // C2158
#pragma make_public(B<int>)   // C2158

void C () {}
#pragma make_public(C)   // C2158

class D {};
#pragma make_public(D)   // OK
```
