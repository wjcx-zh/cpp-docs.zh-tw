---
title: 編譯器警告 (層級 3) C4534
ms.date: 11/04/2016
f1_keywords:
- c4534
helpviewer_keywords:
- C4534
ms.assetid: ec2adf3b-d7a1-4005-bb0c-5d219df78dc8
ms.openlocfilehash: 7d8ff442e84aa7563b1787e5a030297c034e1871
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74992065"
---
# <a name="compiler-warning-level-3-c4534"></a>編譯器警告 (層級 3) C4534

由於預設引數的緣故，' 函式 ' 將不是類別 ' class ' 的預設函式

未受管理的類別可以有具有預設值之參數的函式，而編譯器會使用此函式做為預設的處理常式。 以 `value` 關鍵字標記的類別，不會將其參數的預設值當做預設的函式使用。

如需詳細資訊，請參閱[類別與結構](../../extensions/classes-and-structs-cpp-component-extensions.md)。

下列範例會產生 C4534：

```cpp
// C4534.cpp
// compile with: /W3 /clr /WX
value class MyClass {
public:
   int ii;
   MyClass(int i = 9) {   // C4534, will not be the default constructor
      i++;
   }
};

int main() {
   MyClass ^ xx = gcnew MyClass;
   xx->ii = 0;
}
```
