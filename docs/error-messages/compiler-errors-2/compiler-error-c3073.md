---
title: 編譯器錯誤 C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 0b53e704c14746579a32550726364c062a9ade6f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74756743"
---
# <a name="compiler-error-c3073"></a>編譯器錯誤 C3073

' type '： ref 類別沒有使用者定義的複製函數

在[/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯中，編譯器不會產生參考型別的複製函數。 在任何 **/clr**編譯中，如果您預期要複製類型的實例，則必須針對參考型別定義自己的複製函數。

如需詳細資訊，請參閱[ C++參考型別的堆疊語義](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3073。

```cpp
// C3073.cpp
// compile with: /clr
ref class R {
public:
   R(int) {}
};

ref class S {
public:
   S(int) {}
   S(const S %rhs) {}   // copy constructor
};

void f(R) {}
void f2(S) {}
void f3(R%){}

int main() {
   R r(1);
   f(r);   // C3073
   f3(r);   // OK

   S s(1);
   f2(s);   // OK
}
```
