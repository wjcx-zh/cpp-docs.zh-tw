---
title: 編譯器錯誤 C2893
ms.date: 11/04/2016
f1_keywords:
- C2893
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
ms.openlocfilehash: ca603eb94d5d528a7fed15e0320e1f5d88bf0629
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760872"
---
# <a name="compiler-error-c2893"></a>編譯器錯誤 C2893

無法特殊化函式範本 ' template name '

編譯器無法將函式範本特殊化。 造成此錯誤的原因可能有許多種。

一般來說，解決 C2893 錯誤的方式是檢查函式的簽章，並確定您可以具現化每個型別。

## <a name="example"></a>範例

C2893 發生的原因是 `f`的樣板參數 `T` 推算為 `std::map<int,int>`，但 `std::map<int,int>` 沒有成員 `data_type` （`T::data_type` 無法使用 `T = std::map<int,int>`來具現化）。 下列範例會產生 C2893。

```cpp
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
