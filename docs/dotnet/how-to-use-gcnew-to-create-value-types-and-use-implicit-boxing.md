---
title: HOW TO：使用 gcnew 建立實值型別及使用隱含 Boxing
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: 4b7d0560d8a80d0c09e7f8d0fce83748ec1f2f28
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/11/2019
ms.locfileid: "57739276"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>HOW TO：使用 gcnew 建立實值型別及使用隱含 Boxing

使用[gcnew](../windows/ref-new-gcnew-cpp-component-extensions.md)值型別會建立的 boxed 實的值類型，則可以放在受管理、 記憶體回收堆積。

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

[Boxing](../windows/boxing-cpp-component-extensions.md)
