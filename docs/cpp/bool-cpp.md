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
ms.openlocfilehash: 8cd035686a07285f52fe24aa7ab4f360619d5e1f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87229073"
---
# <a name="bool-c"></a>bool (C++)

這個關鍵字是內建類型。 此類型的變數可以具有值 [`true`](../cpp/true-cpp.md) 和 [`false`](../cpp/false-cpp.md) 。 條件運算式的類型為 **`bool`** ，因此具有類型的值 **`bool`** 。 例如， `i != 0` 現在具有 **`true`** 或， **`false`** 視的值而定 `i` 。

**Visual Studio 2017 15.3 和更新版本**（適用于[/std： c + + 17](../build/reference/std-specify-language-standard-version.md)）：後置或前置遞增或遞減運算子的運算元不可以是類型 **`bool`** 。 換句話說，假設有一個類型為 `b` 的變數 **`bool`** ，則不再允許這些運算式：

```cpp
    b++;
    ++b;
    b--;
    --b;
```

值 **`true`** 和 **`false`** 具有下列關聯性：

```cpp
!false == true
!true == false
```

在下列陳述式中：

```cpp
if (condexpr1) statement1;
```

如果 `condexpr1` 為 **`true`** ， `statement1` 則一律會執行; 如果 `condexpr1` 為 **`false`** ，則永遠不會 `statement1` 執行。

當後置或前置 **`++`** 運算子套用至類型的變數時 **`bool`** ，變數會設定為 **`true`** 。

**Visual Studio 2017 15.3 版和更新**版本： `operator++` for **`bool`** 已從語言中移除，不再受到支援。

後置或前置 **`--`** 運算子不能套用至這個類型的變數。

此 **`bool`** 類型會參與預設的整數提升。 類型的 r 值 **`bool`** 可以轉換成類型的 r 值，而變成零， **`int`** **`false`** 而且 **`true`** 變成一個。 作為相異類型，會 **`bool`** 參與多載解析。

## <a name="see-also"></a>另請參閱

[關鍵字](../cpp/keywords-cpp.md)<br/>
[內建類型](../cpp/fundamental-types-cpp.md)
