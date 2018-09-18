---
title: 編譯器警告 （層級 1） C4572 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4572
dev_langs:
- C++
helpviewer_keywords:
- C4572
ms.assetid: 482dee5a-29bd-4fc3-b769-9dfd4cd2a964
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b87b3dd4264db9fd7ea3699f342358fa6d4d5aac
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076836"
---
# <a name="compiler-warning-level-1-c4572"></a>編譯器警告 (層級 1) C4572

在 /clr 下的 [ParamArray] 屬性已被取代的工作，請使用 '...' 改為

使用指定的變數引數清單的過時樣式。 當編譯為 clr 時，使用省略語法，而不是<xref:System.ParamArrayAttribute>。 如需詳細資訊，請參閱[變數引數清單 （...）(C + + /CLI CLI)](../../windows/variable-argument-lists-dot-dot-dot-cpp-cli.md).

## <a name="example"></a>範例

下列範例會產生 C4572。

```
// C4572.cpp
// compile with: /clr /W1
void Func([System::ParamArray] array<int> ^);   // C4572
void Func2(... array<int> ^){}   // OK

int main() {
   Func2(1, 2, 3);
}
```