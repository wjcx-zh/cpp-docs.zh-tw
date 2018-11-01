---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: 34f9c10cd898b0359463d5933141822576fa4a11
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50485848"
---
# <a name="deprecated-c"></a>deprecated (C++)

本主題是關於 Microsoft 專有 declspec 宣告已被取代。 如需 C + + 14`[[deprecated]]`屬性，以及與 Microsoft 專有 declspec 或 pragma，該屬性的使用時機的指引請參閱[c + + 標準屬性](attributes.md)。

例外狀況，如下所示**過時**宣告可提供相同的功能[已被取代](../preprocessor/deprecated-c-cpp.md)pragma:

- **已被取代**宣告可讓您指定特定形式的函式多載，為已被取代，而 pragma 形式套用至所有的多載形式的函式名稱。

- **已被取代**宣告可讓您指定將在編譯時期顯示的訊息。 訊息的文字可以來自巨集。

- 巨集，才可以標示為使用已被取代**已被取代**pragma。

如果編譯器遇到使用已被取代的識別項或標準[ `[[deprecated]]` ](attributes.md)屬性[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)警告就會擲回。

## <a name="example"></a>範例

下列範例將示範使用 deprecated 函式時，如何將函式標示為取代以及如何指定要在編譯時期顯示的訊息。

```cpp
// deprecated.cpp
// compile with: /W3
#define MY_TEXT "function is deprecated"
void func1(void) {}
__declspec(deprecated) void func1(int) {}
__declspec(deprecated("** this is a deprecated function **")) void func2(int) {}
__declspec(deprecated(MY_TEXT)) void func3(int) {}

int main() {
   func1();
   func1(1);   // C4996
   func2(1);   // C4996
   func3(1);   // C4996
}
```

## <a name="example"></a>範例

下列範例將示範使用 deprecated 類別時，如何將類別標示為取代以及如何指定要在編譯時期顯示的訊息。

```cpp
// deprecate_class.cpp
// compile with: /W3
struct __declspec(deprecated) X {
   void f(){}
};

struct __declspec(deprecated("** X2 is deprecated **")) X2 {
   void f(){}
};

int main() {
   X x;   // C4996
   X2 x2;   // C4996
}
```

## <a name="see-also"></a>另請參閱

[__declspec](../cpp/declspec.md)<br/>
[關鍵字](../cpp/keywords-cpp.md)