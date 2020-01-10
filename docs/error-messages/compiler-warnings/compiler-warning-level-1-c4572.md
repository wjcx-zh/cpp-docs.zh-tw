---
title: 編譯器警告（層級1） C4572
ms.date: 11/04/2016
f1_keywords:
- C4572
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
ms.openlocfilehash: 52285f391af0a8028307cbbc320af33f9cb1fca5
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/12/2019
ms.locfileid: "73965951"
---
# <a name="compiler-warning-level-1-c4572"></a>編譯器警告（層級1） C4572

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