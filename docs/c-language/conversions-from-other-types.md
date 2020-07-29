---
title: 從其他類型轉換
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: bd00bbb8944a0273163fa0c5952be510c9dd697c
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87200331"
---
# <a name="conversions-from-other-types"></a>從其他類型轉換

因為 **`enum`** 值是 **`int`** 根據定義的值，所以與值的轉換 **`enum`** 會與類型相同 **`int`** 。 對於 Microsoft C 編譯器，整數與相同 **`long`** 。

**Microsoft 特定的**

不允許在結構或等位型別之間進行轉換。

任何值都可以轉換成類型 **`void`** ，但這類轉換的結果只能在已捨棄運算式值的內容中使用，例如在運算式語句中。

**`void`** 根據定義，類型沒有任何值。 因此，它無法轉換成任何其他類型，而且其他類型也無法藉 **`void`** 由指派轉換成。 不過，您可以明確地將值轉換為類型 **`void`** ，如[類型](../c-language/type-cast-conversions.md)轉換中所述。

**結束 Microsoft 專有**

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)
