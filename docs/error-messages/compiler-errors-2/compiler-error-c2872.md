---
title: 編譯器錯誤 C2872
ms.date: 11/04/2016
f1_keywords:
- C2872
helpviewer_keywords:
- C2872
ms.assetid: c619ef97-6e0e-41d7-867c-f8d28a07d553
ms.openlocfilehash: f57b250f87bd7f2c5808b5a681ddfe49dfa5e876
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87228891"
---
# <a name="compiler-error-c2872"></a>編譯器錯誤 C2872

'*symbol*'：不明確的符號

編譯器無法判斷您所參考的符號。 範圍內有一個以上具有指定名稱的符號。 請參閱錯誤訊息後面的附注，以取得編譯器找到的不明確符號的檔案位置和宣告。 若要修正這個問題，您可以使用其命名空間（例如或）來完整限定不明確的符號 `std::byte` `::byte` 。 您也可以使用[命名空間別名](../../cpp/namespaces-cpp.md#namespace_aliases)，為包含的命名空間提供方便的簡短名稱，以便在原始程式碼中厘清符號時使用。

如果標頭檔包含[using](../../cpp/namespaces-cpp.md#using_directives)指示詞，則會發生 C2872，並包含後續的標頭檔，其中包含的類型也是指示詞中指定的命名空間 **`using`** 。 **`using`** 只有在使用指定所有標頭檔之後，才指定指示詞 `#include` 。

C2872 可能會在 Visual Studio 2013 中發生，因為 `Windows::Foundation::Metadata::Platform` 列舉類型與 c + +/CX-defined 命名空間之間發生衝突 `Platform` 。 若要解決這個問題，請遵循下列步驟：

- 從專案檔中移除 [使用命名空間 Windows：： Foundation：： Metadata] 子句。

- 為此命名空間中包含的任何類型指定完整名稱。

## <a name="example"></a>範例

下列範例會產生 C2872，因為對名為的變數進行了不明確的參考 `i` ; 具有相同名稱的兩個變數在範圍內：

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
