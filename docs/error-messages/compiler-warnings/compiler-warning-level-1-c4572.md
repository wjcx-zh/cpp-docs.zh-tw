---
title: 編譯器警告 (層級 1) C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: 4a1931032f6d1f8db0679dd782ff2f0ce7ff428c
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80162201"
---
# <a name="compiler-warning-level-1-c4572"></a>編譯器警告 (層級 1) C4572

[ParamArray] 屬性在/clr 下已被取代，請使用 ' ... '只

使用了用於指定變數引數清單的過時樣式。 針對 CLR 編譯時，請使用省略號語法，而不是 <xref:System.ParamArrayAttribute>。 如需詳細資訊，請參閱[Variable 引數清單（...）C++（/cli）](../../extensions/variable-argument-lists-dot-dot-dot-cpp-cli.md)。

## <a name="example"></a>範例

下列範例會產生 C4572。

```cpp
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```
