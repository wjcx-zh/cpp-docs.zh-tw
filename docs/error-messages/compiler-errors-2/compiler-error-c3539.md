---
title: 編譯器錯誤 C3539
ms.date: 11/04/2016
f1_keywords:
- C3539
helpviewer_keywords:
- C3539
ms.assetid: 34a33a0f-d1b6-498f-b312-ffad2d4799b3
ms.openlocfilehash: e30ea0713229bfd8da395baef710571f8dfd49e9
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508153"
---
# <a name="compiler-error-c3539"></a>編譯器錯誤 C3539

' type '：範本引數不能是包含 ' auto ' 的類型

指出的樣板引數類型不能包含關鍵字的使用方式 **`auto`** 。

### <a name="to-correct-this-error"></a>更正這個錯誤

1. 請勿使用關鍵字指定範本引數 **`auto`** 。

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

[auto 關鍵字](../../cpp/auto-cpp.md)
