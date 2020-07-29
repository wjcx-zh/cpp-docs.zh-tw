---
title: 編譯器錯誤 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: 813da5a2fd79c191df731937e58100d749f8690c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87223404"
---
# <a name="compiler-error-c3539"></a>編譯器錯誤 C3539

' type '：範本-引數不可以是包含 ' auto ' 的類型

指定的範本引數類型不能包含關鍵字的用法 **`auto`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿使用關鍵字指定樣板引數 **`auto`** 。

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

## <a name="see-also"></a>另請參閱

[auto 關鍵字](../../cpp/auto-keyword.md)
