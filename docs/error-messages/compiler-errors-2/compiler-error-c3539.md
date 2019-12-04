---
title: 編譯器錯誤 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 85381b237480b86b59c33f02601a1b9dc644a5a4
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761526"
---
# <a name="compiler-error-c3539"></a>編譯器錯誤 C3539

' type '：範本-引數不可以是包含 ' auto ' 的類型

指定的範本引數類型不能包含 `auto` 關鍵字的用法。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 請勿使用 `auto` 關鍵字來指定樣板引數。

## <a name="example"></a>範例

下列範例會產生 C3539。

```cpp
// C3539.cpp
// Compile with /Zc:auto
template<class T> class C{};
int main()
{
   C<auto> c;   // C3539
   return 0;
}
```

## <a name="see-also"></a>請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
