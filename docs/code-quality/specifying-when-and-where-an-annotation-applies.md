---
title: 指定套用註釋的時機和位置
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- _Group_
- _At_
- _When_
- _At_buffer_
ms.assetid: 8e4f4f9c-5dfa-4835-87df-ecd1698fc650
ms.openlocfilehash: 790a1349c3f4d7dbee878f3eb695d83682a7fa7d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87216657"
---
# <a name="specifying-when-and-where-an-annotation-applies"></a>指定套用註釋的時機和位置

當注釋是條件式時，它可能需要其他注釋來指定分析器的批註。  例如，如果函式有可以是同步或非同步變數，函式的行為會如下所示：在同步的情況下，它一律會成功，但在非同步情況下，它會在無法立即成功時報告錯誤。 以同步方式呼叫函式時，檢查結果值不會對程式碼分析器提供任何值，因為它不會傳回。  不過，當以非同步方式呼叫函式，但未檢查函數結果時，可能會發生嚴重的錯誤。 這個範例說明您可以使用批註的情況（如本文 `_When_` 稍後所述）來啟用檢查。

## <a name="structural-annotations"></a>結構化注釋

若要控制批註的套用時機和位置，請使用下列結構化注釋。

|Annotation|說明|
|----------------|-----------------|
|`_At_(expr, anno-list)`|`expr`這是產生左值的運算式。 中的批註 `anno-list` 會套用至所命名的物件 `expr` 。 針對中的每個批註 `anno-list` ， `expr` 如果批註是在前置條件中轉譯，則會在前置條件中解讀，如果批註是在後置條件中轉譯，則會在後置條件中轉譯。|
|`_At_buffer_(expr, iter, elem-count, anno-list)`|`expr`這是產生左值的運算式。 中的批註 `anno-list` 會套用至所命名的物件 `expr` 。 針對中的每個批註 `anno-list` ， `expr` 如果批註在前置條件中被解讀，則會在預先條件中解讀，如果批註是在後置條件中轉譯，則會在後置條件中轉譯。<br /><br /> `iter`這是以注釋為範圍的變數名稱（包含 `anno-list` ）。 `iter`具有隱含類型 **`long`** 。 任何封閉範圍中的名稱相同的變數都會從評估中隱藏出來。<br /><br /> `elem-count`這是評估為整數的運算式。|
|`_Group_(anno-list)`|中的注釋 `anno-list` 全都視為具有套用至每個注釋之群組批註的任何限定詞。|
|`_When_(expr, anno-list)`|`expr`這是可以轉換成的運算式 **`bool`** 。 若為非零（），則會將 **`true`** 中指定的注釋 `anno-list` 視為適用。<br /><br /> 根據預設， `anno-list` `expr` 如果注釋是前置條件，則會將中的每個注釋轉譯為使用輸入值，如果注釋是後置條件，則會使用輸出值。 若要覆寫預設值，您可以在 `_Old_` 評估後置條件時使用內建，以指出應該使用輸入值。 **注意：** `_When_` `*pLength` 由於 `expr` 前置條件中的評估結果可能會與在後置條件中評估的結果不同，因此在使用時，可能會啟用不同的注釋，因為此值會因為先決條件而產生。|

## <a name="see-also"></a>另請參閱

- [使用 SAL 註釋減少 C/C++ 程式碼的缺失](../code-quality/using-sal-annotations-to-reduce-c-cpp-code-defects.md)
- [了解 SAL](../code-quality/understanding-sal.md)
- [註釋函式參數和傳回值](../code-quality/annotating-function-parameters-and-return-values.md)
- [註釋函式行為](../code-quality/annotating-function-behavior.md)
- [註釋結構和類別](../code-quality/annotating-structs-and-classes.md)
- [註釋鎖定行為](../code-quality/annotating-locking-behavior.md)
- [內建函式](../code-quality/intrinsic-functions.md)
- [最佳做法和範例](../code-quality/best-practices-and-examples-sal.md)
