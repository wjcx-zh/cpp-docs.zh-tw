---
title: 編譯器錯誤 C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: f1fad1ad18af54945ef32dadaac50a6de4dbd62f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50455177"
---
# <a name="compiler-error-c2893"></a>編譯器錯誤 C2893

特製化函式樣板 '範本名稱' 失敗

編譯器無法特製化函式樣板。 可以有許多原因造成此錯誤。

一般情況下，C2893 錯誤的解決方法是檢閱函式的簽章，並確定您可以具現化每個型別。

## <a name="example"></a>範例

C2893 發生的原因`f`的範本參數`T`宣告成`std::map<int,int>`，但`std::map<int,int>`沒有成員`data_type`(`T::data_type`不具現化與`T = std::map<int,int>`。)。 下列範例會產生 C2893。

```
// C2893.cpp
// compile with: /c /EHsc
#include<map>
using namespace std;
class MyClass {};

template<class T>
inline typename T::data_type
// try the following line instead
// inline typename  T::mapped_type
f(T const& p1, MyClass const& p2);

template<class T>
void bar(T const& p1) {
    MyClass r;
    f(p1,r);   // C2893
}

int main() {
   map<int,int> m;
   bar(m);
}
```