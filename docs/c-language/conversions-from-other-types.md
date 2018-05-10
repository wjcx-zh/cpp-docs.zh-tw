---
title: 從其他類型轉換 | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- values, converting
- type casts, conversion
ms.assetid: 30fbd974-8f5a-4b70-ac44-d3937b96b702
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e919782022ee64f657611a14d6eae6173a67b8c0
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="conversions-from-other-types"></a>從其他類型轉換

由於 **enum** 值在定義上為 **int** 值，因此在 **enum** 值之間來回轉換的方式與 **int** 類型相同。 對於 Microsoft C 編譯器，整數相當於 **long**。

**Microsoft 特定的**

不允許在結構或等位型別之間進行轉換。

任何值都可以轉換成類型 **void**，不過這類轉換的結果只能在捨棄運算式值的內容中使用，例如運算式陳述式。

**void** 類型在定義上不具任何值。 因此，其無法轉換成任何其他類型，而其他類型也不能藉由指派轉換成 **void**。 不過，您可以將值明確轉換為 **void** 類型，如[類型轉換中所述](../c-language/type-cast-conversions.md)。

**結束 Microsoft 特定的**

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)  
