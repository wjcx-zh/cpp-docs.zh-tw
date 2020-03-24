---
title: 編譯器錯誤 C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 70fc648de8bcf4f1e85edf3a12cc0b7d3d70625f
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201561"
---
# <a name="compiler-error-c2975"></a>編譯器錯誤 C2975

> '*argument*'： '*type*' 的樣板引數無效，應為編譯時期常數運算式

樣板引數與範本宣告不相符;常數運算式應該會出現在角括弧內。 不允許變數做為範本的實際引數。 請檢查樣板定義，以找出正確的類型。

## <a name="example"></a>範例

下列範例會產生 C2975，而且也會顯示正確的使用方式：

```cpp
// C2975.cpp
template<int I>
class X {};

int main() {
   int i = 4, j = 2;
   X<i + j> x1;   // C2975
   X<6> x2;   // OK
}
```

當&#95; &#95;您使用 LINE&#95; &#95;作為具有[/zi](../../build/reference/z7-zi-zi-debug-information-format.md)的編譯時間常數時，也會發生 C2975。 其中一個解決方案是使用[/zi](../../build/reference/z7-zi-zi-debug-information-format.md) （而不是 **/zi**）進行編譯。

```cpp
// C2975b.cpp
// compile with: /ZI
// processor: x86
template<long line>
void test(void) {}

int main() {
   test<__LINE__>();   // C2975
}
```
