---
title: __assume
ms.date: 09/02/2019
f1_keywords:
- __assume
- _assume
- __assume_cpp
helpviewer_keywords:
- __assume keyword [C++]
ms.assetid: d8565123-b132-44b1-8235-5a8c8bff85a7
ms.openlocfilehash: 80acb417ed85ced8f72906848474837efe6bc9d1
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225094"
---
# <a name="__assume"></a>__assume

**Microsoft 特定的**

傳遞提示給最佳化程式。

## <a name="syntax"></a>語法

```C
__assume(
   expression
)
```

### <a name="parameters"></a>參數

*運算式*\
假設評估為 true 的任何運算式。

## <a name="remarks"></a>備註

最佳化程式會在關鍵字出現處假設 `expression` 代表的條件為 true，並保持為 true，直到修改 `expression` (例如，藉由指派給變數) 為止。 選擇性地使用傳遞給優化工具的提示， **`__assume`** 可以改善優化。

如果將 **`__assume`** 語句寫入為衝突（一律評估為 false 的運算式），則一律會將它視為 `__assume(0)` 。 如果您的程式碼未如預期般運作，請確認您定義的 `expression` 有效而且為 true，如先前所述。 如需預期的 `__assume(0)` 行為，請參閱稍後的備註。

> [!WARNING]
> 程式不能在可連線 **`__assume`** 的路徑上包含不正確語句。 如果編譯器可以到達不正確 **`__assume`** 語句，此程式可能會造成無法預期和潛在危險的行為。

`__assume` 不是真的內建函式。 它不需要宣告為函式，且不能用在 `#pragma intrinsic` 指示詞中。 雖然不會產生程式碼，但最佳化程式所產生的程式碼會受到影響。

只有在無法復原判斷提示 **`__assume`** 時，才在[assert](../c-runtime-library/reference/assert-asserte-assert-expr-macros.md)中使用。 請勿 **`__assume`** 在您有後續錯誤復原程式碼的判斷提示中使用，因為編譯器可能會將錯誤處理常式代碼優化。

`__assume(0)` 陳述式是特殊的情況。 使用 `__assume(0)`，表示無法到達的程式碼路徑。 下列範例示範如何使用 `__assume(0)`，表示無法到達 switch 陳述式的 default case。 這會示範 `__assume(0)` 最常見的用法。

為了與舊版相容， **`_assume`** **`__assume`** 除非指定了編譯器選項[/za \( 停用語言擴充](../build/reference/za-ze-disable-language-extensions.md)功能，否則會是同義字。

## <a name="requirements"></a>需求

|內建|架構|
|---------------|------------------|
|**`__assume`**|x86、ARM、x64、ARM64|

## <a name="example"></a>範例

```cpp
// compiler_intrinsics__assume.cpp
#ifdef DEBUG
# define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__) )
#else
# define ASSERT(e)    ( __assume(e) )
#endif

void func1(int i)
{
}

int main(int p)
{
   switch(p){
      case 1:
         func1(1);
         break;
      case 2:
         func1(-1);
         break;
      default:
         __assume(0);
            // This tells the optimizer that the default
            // cannot be reached. As so, it does not have to generate
            // the extra code to check that 'p' has a value
            // not represented by a case arm. This makes the switch
            // run faster.
   }
}
```

使用 `__assume(0)`，告知最佳化程式無法到達 default case。 此範例示範程式設計人員知道 `p` 將僅能輸入 1 或 2。 如果其他值傳入 `p`，程式就會變成無效，並導致無法預期的行為。

做為 `__assume(0)` 陳述式的結果，編譯器不會產生程式碼來測試 `p` 是否有不會呈現在 case 陳述式中的值。 若要完成此運作，`__assume(0)` 陳述式必須是 default case 的主體中的第一個陳述式。

由於編譯器會產生以為基礎的程式碼，因此， **`__assume`** 如果語句中的運算式在 **`__assume`** 執行時間為 false，該程式碼可能無法正確執行。 如果您不確定運算式是否一定會在執行階段為 true，可以使用 `assert` 函式來保護程式碼。

```C
#define ASSERT(e)    ( ((e) || assert(__FILE__, __LINE__)), __assume(e) )
```

不幸的是，這種使用 `assert` 防止編譯器執行 default-case 最佳化，已於本文件稍早所描述。 另一種方法是，可以使用個別的巨集，如下所示。

```C
#ifdef DEBUG
# define NODEFAULT   ASSERT(0)
#else
# define NODEFAULT   __assume(0)
#endif

   default:
      NODEFAULT;
```

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[編譯器內建函式](../intrinsics/compiler-intrinsics.md)\
[關鍵字](../cpp/keywords-cpp.md)
