---
title: 編譯器錯誤 C3633
ms.date: 11/04/2016
f1_keywords:
- C3633
helpviewer_keywords:
- C3633
ms.assetid: 7d65babf-2191-4d67-a69f-f5c4c2ddf946
ms.openlocfilehash: 5f44c94cbb3c945406835816d8fc6ed7c39480eb
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74742622"
---
# <a name="compiler-error-c3633"></a>編譯器錯誤 C3633

無法將 ' member ' 定義為受控 ' type ' 的成員

CLR 參考類別資料成員不可為非 POD C++類型。  您只能具現化 CLR 型別中的 POD 原生型別。  例如，POD 類型不能包含複製的函式或指派運算子。

## <a name="example"></a>範例

下列範例會產生 C3633。

```cpp
// C3633.cpp
// compile with: /clr /c
#pragma warning( disable : 4368 )

class A1 {
public:
   A1() { II = 0; }
   int II;
};

ref class B {
public:
   A1 a1;   // C3633
   A1 * a2;   // OK
   B() : a2( new A1 ) {}
    ~B() { delete a2; }
};
```
