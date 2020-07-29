---
title: 指標類型的轉換
ms.date: 11/04/2016
helpviewer_keywords:
- pointers, converting
- conversions, pointer
- type casts, involving pointers
- void pointers
ms.assetid: 3facc56f-06d3-4570-b1a2-7d4927b83086
ms.openlocfilehash: 6358216e72f054becf33d18aadb6a3a51bab8363
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87218893"
---
# <a name="conversions-to-and-from-pointer-types"></a>指標類型的轉換

一種值類型的指標可以轉換成另一種類型的指標。 不過，由於儲存區中不同類型會有不同的對齊需求和大小，因此結果可能會是未定義。 物件指標可以轉換成類型需要較不嚴格或同等嚴格之儲存對齊的物件指標，並且在不經變更的情況下轉換回原物件指標。

的指標 **`void`** 可以轉換成任何類型的指標，或從任何類型的指標進行轉換，而不會有任何限制或遺失資訊。 如果結果轉換回原始類型，則原始指標會復原。

如果指標轉換成具有相同類型的另一個指標，但是具有不同或額外的限定詞，則新指標會與舊指標相同，不同之處在於新限定詞所施加的限制。

指標值也可以轉換成整數值。 根據下列規則，轉換路徑取決於指標的大小和整數類資料類型的大小：

- 如果指標的大小大於或等於整數類資料類型的大小，則指標的行為會像是轉換中不帶正負號的值，不過它不能轉換成浮點值。

- 如果指標小於整數類資料類型，則指標會先轉換成與整數類資料類型具有相同大小的指標，然後再轉換成整數類資料類型。

相反地，根據下列規則，整數類資料類型可以轉換成指標類型：

- 如果整數類資料類型與指標類型的大小相同，則轉換只會導致將整數值視為指標 (不帶正負號的整數)。

- 如果整數類型的大小與指標類型不相同，則會先使用[從帶正負號整數類型的轉換](../c-language/conversions-from-signed-integral-types.md)和[從不帶正負號整類型的轉換](../c-language/conversions-from-unsigned-integral-types.md)中所提供的轉換路徑，將整數類型轉換成指標的大小。 然後才會將它視為指標值。

值為0的整數常數運算式，或這類運算式轉換成類型， **`void`** <strong>\*</strong> 可以透過類型轉換、指派或與任何類型的指標比較來進行轉換。 這樣所產生的 null 指標相當於相同類型的另一個 null 指標，但是這個 null 指標不等於任何函式指標或物件指標。 常數 0 以外的整數可以轉換成指標類型，但是結果不可移植。

## <a name="see-also"></a>另請參閱

[指派轉換](../c-language/assignment-conversions.md)
