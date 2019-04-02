---
title: HOW TO：使用 gcnew 建立實值型別及使用隱含 Boxing
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: c67f8e0b9511f4ed1610e72e4a7df41c949b1d27
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/01/2019
ms.locfileid: "58770790"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>HOW TO：使用 gcnew 建立實值型別及使用隱含 Boxing

使用[gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md)值型別會建立的 boxed 實的值類型，則可以放在受管理、 記憶體回收堆積。

## <a name="example"></a>範例

```
// vcmcppv2_explicit_boxing4.cpp
// compile with: /clr
public value class V {
public:
   int m_i;
   V(int i) : m_i(i) {}
};

public ref struct TC {
   void do_test(V^ v) {
      if (v != nullptr)
         ;
      else
         ;
   }
};

int main() {
   V^ v = gcnew V(42);
   TC^ tc = gcnew TC;
   tc->do_test(v);
}
```

## <a name="see-also"></a>另請參閱

[Boxing](../extensions/boxing-cpp-component-extensions.md)
