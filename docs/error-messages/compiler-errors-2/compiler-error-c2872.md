---
title: 編譯器錯誤 C2872 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2872
dev_langs:
- C++
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 038c3475a6041dfb719bb2270a87ac2898f8b958
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036750"
---
# <a name="compiler-error-c2872"></a>編譯器錯誤 C2872

'*符號*': 模稜兩可的符號

編譯器無法判斷在參考的符號。 具有指定名稱的多個符號位於範圍內。 請參閱下列的檔案位置和宣告的錯誤訊息的附註編譯器發現模稜兩可的符號。 若要修正此問題，您可以完整限定的模稜兩可的符號使用它的命名空間，例如`std::byte`或`::byte`。 您也可以使用[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)釐清您的程式碼中的符號的使用者內含的命名空間提供方便的簡短名稱，供使用。

如果包含的標頭檔，就會發生 C2872 [using 指示詞](../../cpp/namespaces-cpp.md#using_directives)，和後續的標頭檔會包含在所包含的類型，也是在指定的命名空間中`using`指示詞。 指定`using`指示詞只是在所有標頭檔案由指定之後`#include`。

如需 C2872 的詳細資訊，請參閱知識庫文件[PRB： 編譯器錯誤當您使用 #import Visual c + +.NET 中的 XML](http://support.microsoft.com/kb/316317)和["錯誤 C2872: 'Platform': 模稜兩可的符號 」 使用時，會產生錯誤訊息。在 Visual Studio 2013 的 Windows::Foundation::Metadata 命名空間](https://support.microsoft.com/kb/2890859)。

## <a name="example"></a>範例

下列範例會產生 C2872，因為模稜兩可的參考對變數，名為`i`; 兩個具有相同名稱的變數是在範圍內：

```cpp
// C2872.cpp
// compile with: cl /EHsc C2872.cpp
namespace A {
   int i;
}

using namespace A;
int i;
int main() {
   ::i++;   // ok, uses i from global namespace
   A::i++;   // ok, uses i from namespace A
   i++;   // C2872 ambiguous: ::i or A::i?
   // To fix this issue, use the fully qualified name
   // for the intended variable.
}
```