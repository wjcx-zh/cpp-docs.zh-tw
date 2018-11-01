---
title: 轉型運算子
ms.custom: index-page
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C++], casting
- casting operators [C++]
ms.assetid: 16240348-26bc-4f77-8eab-57253f00ce52
ms.openlocfilehash: 4d6c8a0dc448e08ae2f344faeeb27756cdd27eff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50549743"
---
# <a name="casting-operators"></a>轉型運算子

C++ 語言有幾個特有的轉型運算子。 這些運算子的目的在於移除舊式 C 語言轉型固有的模稜兩可和危險。 這些運算子如下所列：

- [dynamic_cast](../cpp/dynamic-cast-operator.md)用於多型類型的轉換。

- [static_cast](../cpp/static-cast-operator.md)用於非多型類型的轉換。

- [const_cast](../cpp/const-cast-operator.md)用來移除**const**， **volatile**，和 **__unaligned**屬性。

- [reinterpret_cast](../cpp/reinterpret-cast-operator.md)用於簡單精進的位元。

- [safe_cast](../windows/safe-cast-cpp-component-extensions.md)用來產生可驗證的 MSIL。

使用**const_cast**並**reinterpret_cast**做最後的手段，因為這些運算子存在相同危險與舊類型轉換。 然而，為了完全取代舊類型轉換，這些運算子仍有其必要。

## <a name="see-also"></a>另請參閱

[轉型](../cpp/casting.md)