---
title: bool (C++)
ms.date: 11/04/2016
f1_keywords:
- bool_cpp
- __BOOL_DEFINED
helpviewer_keywords:
- bool keyword [C++]
- __BOOL_DEFINED macro
ms.assetid: 9abed3f2-d21c-4eb4-97c5-716342e613d8
ms.openlocfilehash: db246cda79c778f37c5afbfda4a68c191c474e12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190491"
---
# <a name="bool-c"></a>bool (C++)

這個關鍵字是內建類型。 此類型的變數可以有[true](../cpp/true-cpp.md)和[false](../cpp/false-cpp.md)的值。 條件運算式的類型為**bool** ，因此具有**bool**類型的值。 例如，根據 `i`的值，`i!=0` 現在會有 TRUE 或 FALSE。

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：後置或前置遞增或遞減運算子的運算元不可以是**bool**類型。 換句話說，假設變數 `b` 類型為**bool**，則不再允許使用這些運算式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```

TRUE 和 FALSE 值具有下列關聯性：

```cpp
!false == true
!true == false
```

在下列陳述式中：

```cpp
if (condexpr1) statement1;
```

如果 `condexpr1` 為 TRUE，則一律會執行 `statement1`;如果 `condexpr1` 為 FALSE，則永遠不會執行 `statement1`。

當後置或前置詞 **++** 運算子套用至**bool**類型的變數時，變數會設定為 TRUE。
**Visual Studio 2017 15.3 版和更新**版本： **bool**的 operator + + 已從語言中移除，不再受到支援。

後置或前置詞 **--** 運算子不能套用至這個類型的變數。

**Bool**類型會參與整數提升。 **Bool**類型的 r 值可以轉換成**int**類型的 r 值，而 FALSE 會變成零，而 TRUE 則變成一個。 作為相異類型， **bool**會參與多載解析。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[內建類型](../cpp/fundamental-types-cpp.md)
