---
title: 編譯器錯誤 C2760
ms.date: 11/04/2016
f1_keywords:
- C2760
helpviewer_keywords:
- C2760
ms.assetid: 585757fd-d519-43f3-94e5-50316ac8b90b
ms.openlocfilehash: 5680de2fe0364d7cdc5e7ef017bd298423ea4c21
ms.sourcegitcommit: fd0f8839da5c6a3663798a47c6b0bb6e63b518bd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70273660"
---
# <a name="compiler-error-c2760"></a>編譯器錯誤 C2760

> 語法錯誤: 必須是 '*name1*' 而不是 '*name2*'

## <a name="remarks"></a>備註

有數種方式可造成此錯誤。 通常, 這是由編譯器無法理解的 token 順序所造成。

## <a name="example"></a>範例

在此範例中, 轉型運算子與不正確運算子搭配使用。

```cpp
// C2760.cpp
class B {};
class D : public B {};

void f(B* pb) {
    D* pd1 = static_cast<D*>(pb);
    D* pd2 = static_cast<D*>=(pb);  // C2760
    D* pd3 = static_cast<D*=(pb);   // C2760
}
```
