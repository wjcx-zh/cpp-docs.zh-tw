---
title: 編譯器錯誤 C2061
ms.date: 11/04/2016
f1_keywords:
- C2061
helpviewer_keywords:
- C2061
ms.assetid: b0e61c0c-a205-4820-b9aa-301d6c6fe6eb
ms.openlocfilehash: 85357d94c7bc2d709e852daa60caf269949ad1b8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408689"
---
# <a name="compiler-error-c2061"></a>編譯器錯誤 C2061

語法錯誤： 識別項 'identifier'

編譯器發現之識別項，它不預期的位置。 請確定`identifier`宣告才能使用它。

初始設定式可能會以括號括住。 若要避免這個問題，括號括住宣告子，或使它`typedef`。

當編譯器偵測到的運算式做為類別範本引數; 也會發生此錯誤使用  [typename](../../cpp/typename.md)告訴編譯器為型別。

下列範例會產生 C2061:

```
// C2061.cpp
// compile with: /c
template < A a >   // C2061
// try the following line instead
// template < typename b >
class c{};
```

如果您傳遞至執行個體名稱，就會發生 C2061 [typeid](../../extensions/typeid-cpp-component-extensions.md):

```
// C2061b.cpp
// compile with: /clr
ref struct G {
   int i;
};

int main() {
   G ^ pG = gcnew G;
   System::Type ^ pType = typeid<pG>;   // C2061
   System::Type ^ pType2 = typeid<G>;   // OK
}
```