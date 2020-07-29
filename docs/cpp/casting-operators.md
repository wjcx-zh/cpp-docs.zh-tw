---
title: 轉型運算子
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 606e8b159bb7bdb7527d33a5211cb33a26913754
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87221818"
---
# <a name="casting-operators"></a>轉型運算子

C++ 語言有幾個特有的轉型運算子。 這些運算子的目的在於移除舊式 C 語言轉型固有的模稜兩可和危險。 這些運算子如下所列：

- [dynamic_cast](../cpp/dynamic-cast-operator.md)用於多型類型的轉換。

- [static_cast](../cpp/static-cast-operator.md)用於非多型類型的轉換。

- [const_cast](../cpp/const-cast-operator.md)用來移除 **`const`** 、 **`volatile`** 和 **`__unaligned`** 屬性。

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用於位的簡單 reinterpretation。

- [safe_cast](../extensions/safe-cast-cpp-component-extensions.md)在 c + +/CLI 中用來產生可驗證的 MSIL。

**`const_cast`** 請使用和 **`reinterpret_cast`** 做為最後的手段，因為這些運算子會與舊的樣式轉換呈現相同的危險。 然而，為了完全取代舊類型轉換，這些運算子仍有其必要。

## <a name="see-also"></a>另請參閱

[轉型](../cpp/casting.md)
