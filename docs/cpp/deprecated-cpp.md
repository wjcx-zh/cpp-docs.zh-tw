---
title: deprecated (C++)
ms.date: 03/28/2017
f1_keywords:
- deprecated_cpp
helpviewer_keywords:
- __declspec keyword [C++], deprecated
- deprecated __declspec keyword
ms.assetid: beef1129-9434-4cb3-8392-f1eb29e04805
ms.openlocfilehash: e4689d3cb1a1757e2ac3bf4ca9eef7670ad5c655
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189477"
---
# <a name="deprecated-c"></a>deprecated (C++)

本主題是關於 Microsoft 特定的已淘汰 declspec 宣告。 如需 c + + 14 `[[deprecated]]` 屬性的詳細資訊，以及使用該屬性的時機與 Microsoft 特定 declspec 或 pragma 的相關指引，請參閱[ C++標準屬性](attributes.md)。

有了下面所述的例外狀況，已被**取代**的宣告會提供與已[淘汰](../preprocessor/deprecated-c-cpp.md)pragma 相同的功能：

- 已**取代**的宣告可讓您將特定形式的函式多載指定為已被取代，而 pragma 格式則適用于函式名稱的所有多載形式。

- 已**取代**的宣告可讓您指定將在編譯時期顯示的訊息。 訊息的文字可以來自巨集。

- 宏只能標記為已被**取代**的 pragma。

如果編譯器遇到使用已被取代的識別碼或標準[`[[deprecated]]`](attributes.md)屬性，則會擲回[C4996](../error-messages/compiler-warnings/compiler-warning-level-3-c4996.md)警告。

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
