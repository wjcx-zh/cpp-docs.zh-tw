---
title: 編譯器錯誤 C3072
ms.date: 11/04/2016
f1_keywords:
- C3072
helpviewer_keywords:
- C3072
ms.assetid: cdd5cb6b-c478-4698-adfa-c40188d34a18
ms.openlocfilehash: a8fe0802a7529551fce1c0b7242c867db52d8842
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756756"
---
# <a name="compiler-error-c3072"></a>編譯器錯誤 C3072

無法將運算子 ' operator ' 套用至 ref 類別的實例

使用一元 '`operator` ' 運算子將 ref 類別的實例轉換為控制碼類型

CLR 類型需要 CLR 運算子，而不是原生（或標準）運算子。  如需詳細資訊，請參閱[追蹤參考運算子](../../extensions/tracking-reference-operator-cpp-component-extensions.md)。

## <a name="example"></a>範例

下列範例會產生 C3072。

```cpp
// C3072.cpp
// compile with: /clr
ref class R {};

int main() {
   R r1;
   R^ r2 = &r1;   // C3072
   R^ r3 = %r1;   // OK
}
```
