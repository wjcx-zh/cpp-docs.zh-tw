---
title: 編譯器警告 C4984
ms.date: 08/19/2019
f1_keywords:
- C4984
helpviewer_keywords:
- C4984
ms.openlocfilehash: 91ae30018c7de633d8ba23d538b301ad4bbac984
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2019
ms.locfileid: "69632902"
---
# <a name="compiler-warning-c4984"></a>編譯器警告 C4984

> ' if constexpr ' 是 c + + 17 語言延伸模組

## <a name="remarks"></a>備註

編譯器會在程式`if constexpr`代碼中找到使用預設 c + + 14 標準編譯的運算式。 這個運算式是從 c + + 17 標準開始指定。 如果您需要 c + + 11 或 c + + 14 相容性, 則此運算式無法移植。

預設會將 C4984 發行為錯誤, 但它是 suppressible。 若要將您的程式碼編譯為 c + + 17 來啟用此運算式, 請使用[/std: c + + 17 或/std: c + + 最新版本](../../build/reference/std-specify-language-standard-version.md) 若要在`if constexpr`以 c + + 14 編譯的程式碼中使用運算式做為 Microsoft 擴充功能, 您可以隱藏、停用或變更錯誤訊息的警告層級。 您可以使用[/wd4984](../../build/reference/compiler-option-warning-level.md)來停用 C4984 或 __/w__*n*__4984__ , 將它啟用為層級*N*警告, 而不是錯誤。 或者, 在原始程式檔中產生警告的那一行之前, 使用[#pragma 警告 (隱藏: 4984)](../../preprocessor/warning.md) 。

從 Visual Studio 2017 15.3 版開始, 會提供此警告。 如需如何停用在特定編譯器版本或更新版本中引進之警告的相關資訊, 請參閱編譯器[版本的編譯器警告](compiler-warnings-by-compiler-version.md)。

## <a name="example"></a>範例

這個範例會產生 C4984, 並顯示修正方法:

```cpp
// C4984.cpp
// compile with: cl /EHsc C4984.cpp
#include <iostream>

int main()
{
    constexpr bool compile_time = true;
    // Uncomment the following line or use /std:c++17 to fix
    // #pragma warning(suppress:4984)
    if constexpr (compile_time)
    {
        std::cout << "compile_time is true";
    }
    else
    {
        std::cout << "compile_time is false";
    }
}
```
