---
title: deprecated pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 2e76d1c53cb900c108e2839a9aad17b330143a5d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222398"
---
# <a name="deprecated-pragma"></a>deprecated pragma

已**淘汰**的 pragma 可讓您指出未來版本中可能不再支援的函式、類型或任何其他識別碼, 或不應再使用。

> [!NOTE]
> 如需 c + + 14 `[[deprecated]]`屬性的詳細資訊, 以及使用該屬性而非 Microsoft `__declspec(deprecated)`修飾詞或已被**取代**之 pragma 的指引, 請參閱[中C++的屬性](../cpp/attributes.md)。

## <a name="syntax"></a>語法

> **#pragma 已被取代 (** *identifier1* [ **,** *identifier2* ...] **)**

## <a name="remarks"></a>備註

當編譯器遇到已被**取代**的 pragma 所指定的識別碼時, 會發出編譯器警告[C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md)。

您可以取代巨集名稱。 為巨集名稱加上引號，否則會發生巨集展開。

因為已**淘汰**的 pragma 適用于所有相符的識別碼, 而且不會將簽章納入考慮, 所以不是淘汰特定版本的多載函式的最佳選項。 帶入範圍中的任何相符函數名稱都會觸發警告。

我們建議您盡可能使用 c + `[[deprecated]]` + 14 屬性, 而不是已被**取代**的 pragma。 在許多情況下, Microsoft 特有的[__declspec (已淘汰)](../cpp/deprecated-cpp.md)宣告修飾詞也是比被**取代**的 pragma 更好的選擇。 `[[deprecated]]`屬性和`__declspec(deprecated)`修飾詞可讓您針對特定形式的多載函式指定已被取代的狀態。 只有當屬性或修飾詞套用至特定多載函式的參考時, 診斷警告才會出現。

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

[Pragma 指示詞和 __pragma 關鍵字](../preprocessor/pragma-directives-and-the-pragma-keyword.md)