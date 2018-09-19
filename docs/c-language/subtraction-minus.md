---
title: 減法 (-) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], subtraction
- subtraction operator, syntax
ms.assetid: 9cacba7d-20b3-4372-8a63-ba5d8ee64177
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8b09683592ca7fe897c8477a17c14fbc72d11f7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46079956"
---
# <a name="subtraction--"></a>減法 (-)

減法運算子 (**-**) 會從第一個運算元減去第二個。 這兩個運算元都可以是整數類資料類型或浮點類型，或是一個運算元為指標，另一個為整數。

當兩個指標都減去時，就會藉由將差數除以指標定址之類型值的大小，將差數轉換成帶正負號的整數值。 整數值的大小是由標準 Include 檔 STDDEF.H 中的 **ptrdiff_t** 類型所定義。 結果代表該類型在兩個位址之間的記憶體位置數目。 這個結果只保證對相同陣列的兩個項目具有意義，如[指標算術](../c-language/pointer-arithmetic.md)中所述。

從指標值減去整數值時，減法運算子會藉由將整數值 (*i*) 乘以指標所定址之值的大小進行整數值轉換。 在轉換之後，整數值代表 *i* 個記憶體位置，其中每個位置的長度都是以指標類型指定。 從指標值中減去轉換的整數值時，結果會是原始位址之前記憶體位址的 *i* 個位置。 新指標會指向原始指標值所定址類型的值。

## <a name="see-also"></a>請參閱

[C 加法類運算子](../c-language/c-additive-operators.md)