---
title: 編譯器錯誤 C3073
ms.date: 11/04/2016
f1_keywords:
- C3073
helpviewer_keywords:
- C3073
ms.assetid: b24b9b8b-f9fb-4c3c-a1a0-97fad2081bfc
ms.openlocfilehash: 8a4a2011124056af7064c8241450e1f3613776a9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62406700"
---
# <a name="compiler-error-c3073"></a>編譯器錯誤 C3073

'type': ref 類別沒有使用者定義的複製建構函式

在  [/clr （Common Language Runtime 編譯）](../../build/reference/clr-common-language-runtime-compilation.md)編譯時，編譯器不會產生參考類型的複製建構函式。 在任何 **/clr**編譯時，您必須定義您自己的複製建構函式的參考型別，如果您預期要複製之型別的執行個體。

如需詳細資訊，請參閱 < [ C++的參考型別堆疊語意](../../dotnet/cpp-stack-semantics-for-reference-types.md)。

## <a name="example"></a>範例

下列範例會產生 C3073。

```
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