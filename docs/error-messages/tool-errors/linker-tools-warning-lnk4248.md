---
title: 連結器工具警告 LNK4248
ms.date: 11/04/2016
f1_keywords:
- LNK4248
helpviewer_keywords:
- LNK4248
ms.assetid: e40523ff-e3cb-4ba6-ab79-23f0f339f6cf
ms.openlocfilehash: 4ba05ef067c539dc9c0aca6dc2a395748fd217a2
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2019
ms.locfileid: "74988108"
---
# <a name="linker-tools-warning-lnk4248"></a>連結器工具警告 LNK4248

' type ' 的無法解析的 typeref 標記（token）;映射可能無法執行

類型在 MSIL 中繼資料中沒有定義。

當 MSIL 模組中只有一個類型的向前宣告（以 **/clr**編譯），其中類型在 msil 模組中被參考，而且 msil 模組與具有該類型定義的原生模組連結時，就會發生 LNK4248。

在此情況下，連結器將會在 MSIL 中繼資料中提供原生類型定義，而這可能會提供正確的行為。

不過，如果轉送類型宣告是 CLR 類型，則連結器的原生類型定義可能不正確

如需詳細資訊，請參閱 [/clr (Common Language Runtime 編譯)](../../build/reference/clr-common-language-runtime-compilation.md)。

### <a name="to-correct-this-error"></a>若要改正這項錯誤

1. 在 MSIL 模組中提供類型定義。

## <a name="example"></a>範例

下列範例會產生 LNK4248。 定義要解析的結構 A。

```cpp
// LNK4248.cpp
// compile with: /clr /W1
// LNK4248 expected
struct A;
void Test(A*){}

int main() {
   Test(0);
}
```

## <a name="example"></a>範例

下列範例具有類型的向前定義。

```cpp
// LNK4248_2.cpp
// compile with: /clr /c
class A;   // provide a definition for A here to resolve
A * newA();
int valueA(A * a);

int main() {
   A * a = newA();
   return valueA(a);
}
```

## <a name="example"></a>範例

下列範例會產生 LNK4248。

```cpp
// LNK4248_3.cpp
// compile with: /c
// post-build command: link LNK4248_2.obj LNK4248_3.obj
class A {
public:
   int b;
};

A* newA() {
   return new A;
}

int valueA(A * a) {
   return (int)a;
}
```
