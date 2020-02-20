---
title: /Zc:rvalueCast (強制型別轉換規則)
ms.date: 02/18/2020
f1_keywords:
- rvaluecast
- /Zc:rvalueCast
- VC.Project.VCCLCompilerTool.EnforceTypeConversionRules
helpviewer_keywords:
- -Zc compiler options (C++)
- rvaluecast
- Enforce type conversion rules
- /Zc compiler options (C++)
- Zc compiler options (C++)
ms.assetid: 7825277d-e565-4c48-b0fb-76ac0b0c6e38
ms.openlocfilehash: ac74192cad8a62e4c82b480038e727b114362cdd
ms.sourcegitcommit: b9aaaebe6e7dc5a18fe26f73cc7cf5fce09262c1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77504568"
---
# <a name="zcrvaluecast-enforce-type-conversion-rules"></a>/Zc:rvalueCast (強制型別轉換規則)

指定 **`/Zc:rvalueCast`** 選項時，編譯器會正確地將右值參考型別識別為轉換運算的結果。 其行為符合 c + + 11 標準。 未指定選項時，編譯器行為會與 Visual Studio 2012 中的相同。

## <a name="syntax"></a>語法

> **`/Zc:rvalueCast`**\
> **`/Zc:rvalueCast-`**

## <a name="remarks"></a>備註

如果指定了 **`/Zc:rvalueCast`** ，編譯器會遵循 c + + 11 標準的第5.4 節，並且只會將產生非參考型別和轉型運算式的轉型運算式，視為將非函式類型的右值參考當做右數值型別。 根據預設，或如果指定了 **`/Zc:rvalueCast-`** ，則編譯器會不符合規範，並會將導致右值參考的所有 cast 運算式視為右值。 為了符合規範，並在使用轉換時排除錯誤，建議您使用 **`/Zc:rvalueCast`** 。

根據預設， **`/Zc:rvalueCast`** 為關閉（ **`/Zc:rvalueCast-`** ）。 [/Permissive-](permissive-standards-conformance.md)編譯器選項會隱含設定此選項，但可以使用 **`/Zc:rvalueCast-`** 來加以覆寫。

如果您將 cast 運算式當做引數傳遞至採用右值參考型別的函式，請使用 **`/Zc:rvalueCast`** 。 當編譯器不正確地判斷 cast 運算式的類型時，預設行為會導致編譯器錯誤[C2664](../../error-messages/compiler-errors-2/compiler-error-c2664.md) 。 這個範例會在未指定 **`/Zc:rvalueCast`** 時，顯示正確程式碼中的編譯器錯誤：

```cpp
// Test of /Zc:rvalueCast
// compile by using:
// cl /c /Zc:rvalueCast- make_thing.cpp
// cl /c /Zc:rvalueCast make_thing.cpp

#include <utility>

template <typename T>
struct Thing {
   // Construct a Thing by using two rvalue reference parameters
   Thing(T&& t1, T&& t2)
      : thing1(t1), thing2(t2) {}

   T& thing1;
   T& thing2;
};

// Create a Thing, using move semantics if possible
template <typename T>
Thing<T> make_thing(T&& t1, T&& t2)
{
   return (Thing<T>(std::forward<T>(t1), std::forward<T>(t2)));
}

struct Test1 {
   long a;
   long b;

   Thing<long> test() {
      // Use identity casts to create rvalues as arguments
      return make_thing(static_cast<long>(a), static_cast<long>(b));
   }
};
```

適當時，預設編譯器行為可能不會報告錯誤 C2102。 在此範例中，如果未指定 **`/Zc:rvalueCast`** 時，則編譯器不會報告錯誤：

```cpp
int main() {
   int a = 1;
   int *p = &a;   // Okay, take address of lvalue
                  // Identity cast creates rvalue from lvalue;
   p = &(int)a;   // problem: should cause C2102: '&' requires l-value
}
```

如需 Visual C++ 中一致性問題的詳細資訊，請參閱 [Nonstandard Behavior](../../cpp/nonstandard-behavior.md)。

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>在 Visual Studio 開發環境中設定這個編譯器選項

1. 開啟專案的 [屬性頁] 對話方塊。 如需詳細資訊，請參閱[在 Visual Studio 中設定 C ++ 編譯器和組建屬性](../working-with-project-properties.md)。

1.  > [ **C/C++**  > **語言**] 屬性頁中選取 [設定**屬性**]。

1. 將 [**強制型別轉換規則**] 屬性設定為 **`/Zc:rvalueCast`** 或 **`/Zc:rvalueCast-`** 。 選擇 **[確定]** **或 [** 套用] 以儲存變更。

## <a name="see-also"></a>另請參閱

[/Zc (一致性)](zc-conformance.md)
