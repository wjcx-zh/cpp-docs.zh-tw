---
title: 從其他類型轉換
ms.date: 01/29/2018
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
ms.openlocfilehash: f9f2d73e57c576dcf8afed008a74e5e7dd9b9d6f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62312462"
---
# <a name="conversions-from-other-types"></a>從其他類型轉換

由於 **enum** 值在定義上為 **int** 值，因此在 **enum** 值之間來回轉換的方式與 **int** 類型相同。 對於 Microsoft C 編譯器，整數相當於 **long**。

**Microsoft 特定的**

不允許在結構或等位型別之間進行轉換。

任何值都可以轉換成類型 **void**，不過這類轉換的結果只能在捨棄運算式值的內容中使用，例如運算式陳述式。

**void** 類型在定義上不具任何值。 因此，其無法轉換成任何其他類型，而其他類型也不能藉由指派轉換成 **void**。 不過，您可以將值明確轉換為 **void** 類型，如[類型轉換中所述](../c-language/type-cast-conversions.md)。

**結束 Microsoft 專有**

## <a name="see-also"></a>請參閱

[指派轉換](../c-language/assignment-conversions.md)
