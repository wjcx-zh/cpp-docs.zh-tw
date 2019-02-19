---
title: 加法 (+)
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, adding integers
ms.assetid: b9014fee-825d-46ef-91db-5d46807081fc
ms.openlocfilehash: 48672315960e32cb324aacc6c90d3d67891f3d39
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/12/2019
ms.locfileid: "56149878"
---
# <a name="addition-"></a>加法 (+)

加法運算子 (**+**) 會使它的兩個運算元相加。 這兩個運算元都可以是整數類資料類型或浮點類型，或是一個運算元為指標，另一個為整數。

當整數與指標相加時，會藉由將整數值 (*i*) 乘以指標所定址之值的大小，以進行整數值轉換。 在轉換之後，整數值代表 *i* 個記憶體位置，其中每個位置的長度都是以指標類型指定。 當轉換的整數值與指標值相加時，結果會是新的指標值，代表來自原始位址的位址 *i* 位置。 新的指標值會將相同類型的值定址為原始指標值，因此與陣列索引相同 (請參閱[一維陣列](../c-language/one-dimensional-arrays.md)和[多維陣列](../c-language/multidimensional-arrays-c.md))。 如果總和指標指向陣列外部，但在高位階之外的第一個位置除外，則結果會是未定義。 如需詳細資訊，請參閱[指標算術](../c-language/pointer-arithmetic.md)。

## <a name="see-also"></a>另請參閱

[C 加法類運算子](../c-language/c-additive-operators.md)
