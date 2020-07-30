---
title: deprecated pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 52d9deb4ad68dacc99fab9d12bc9eb21bc0d360e
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87231607"
---
# <a name="deprecated-pragma"></a>deprecated pragma

**`deprecated`** Pragma 可讓您指出未來版本中可能不再支援函式、類型或任何其他識別碼，或不再使用。

> [!NOTE]
> 如需 c + + 14 屬性的詳細資訊 `[[deprecated]]` ，以及使用該屬性而非 Microsoft 修飾詞 `__declspec(deprecated)` 或 pragma 的指引 **`deprecated`** ，請參閱[c + + 中的屬性](../cpp/attributes.md)。

## <a name="syntax"></a>語法

> **#pragma 已被取代（** *identifier1* [ **，** *identifier2* ...] **）**

## <a name="remarks"></a>備註

當編譯器遇到 pragma 所指定的識別碼時 **`deprecated`** ，會發出編譯器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。

您可以取代巨集名稱。 為巨集名稱加上引號，否則會發生巨集展開。

由於 **`deprecated`** pragma 適用于所有相符的識別碼，而且不會將簽章納入考慮，因此它不是淘汰特定版本的多載函式的最佳選項。 帶入範圍中的任何相符函數名稱都會觸發警告。

我們建議您盡可能使用 c + + 14 `[[deprecated]]` 屬性，而不是 **`deprecated`** pragma。 在許多情況下，Microsoft 專有的[__declspec （已淘汰）](../cpp/deprecated-cpp.md)宣告修飾詞也是較佳的選擇，而不是 **`deprecated`** pragma。 `[[deprecated]]`屬性和修飾詞可 `__declspec(deprecated)` 讓您針對特定形式的多載函式指定已被取代的狀態。 只有當屬性或修飾詞套用至特定多載函式的參考時，診斷警告才會出現。

## <a name="example"></a>範例

```cpp
// pragma_directive_deprecated.cpp
// compile with: /W3
#include <stdio.h>
void func1(void) {
}

void func2(void) {
}

int main() {
   func1();
   func2();
   #pragma deprecated(func1, func2)
   func1();   // C4995
   func2();   // C4995
}
```

下列範例將示範如何取代類別：

```cpp
// pragma_directive_deprecated2.cpp
// compile with: /W3
#pragma deprecated(X)
class X {  // C4995
public:
   void f(){}
};

int main() {
   X x;   // C4995
}
```

## <a name="see-also"></a>另請參閱

[Pragma 指示詞與 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
