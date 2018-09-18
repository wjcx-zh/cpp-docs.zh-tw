---
title: 編譯器錯誤 C2893 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2893
dev_langs:
- C++
helpviewer_keywords:
- C2893
ms.assetid: ec0cbe43-005d-45da-8742-aaeb9b81d28e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73d4f838f030db3667b08295006c2ea1df94c87b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46026175"
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