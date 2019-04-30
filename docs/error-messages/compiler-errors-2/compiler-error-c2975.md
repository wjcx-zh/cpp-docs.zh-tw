---
title: 編譯器錯誤 C2975
ms.date: 11/04/2016
f1_keywords:
- C2975
helpviewer_keywords:
- C2975
ms.assetid: 526f6b9d-6c76-4c12-9252-1b1d7c1e06c7
ms.openlocfilehash: 66b7c0d61cbc8141b9ed3e5f6eb329b68eb00477
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2019
ms.locfileid: "64344694"
---
# <a name="compiler-error-c2975"></a>編譯器錯誤 C2975

> '*引數*': 無效的樣板引數的'*型別*'，必須是編譯時期常數運算式

樣板引數不符合樣板宣告中;常數運算式，應該會出現在角括號內。 變數不允許作為範本的實際引數。 請檢查樣板定義，以找出正確的類型。

## <a name="example"></a>範例

下列範例會產生 C2975，並也會示範正確使用方式：

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

當您使用時，也會發生 C2975 &#95;&#95;行&#95;&#95;做為編譯時間常數，與[/ZI](../../build/reference/z7-zi-zi-debug-information-format.md)。 一個解決方案是使用編譯[/Zi](../../build/reference/z7-zi-zi-debug-information-format.md)而不是 **/ZI**。

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