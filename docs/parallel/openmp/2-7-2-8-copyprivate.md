---
title: 2.7.2.8 copyprivate
ms.date: 11/04/2016
ms.assetid: c382348c-c785-45b2-8ee6-a66b76b97f3e
ms.openlocfilehash: d4df1b4216014d3cd15be1480d2f83334fddb72d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50622907"
---
# <a name="2728-copyprivate"></a>2.7.2.8 copyprivate

**Copyprivate**子句提供一個機制來使用私用變數從一小組的成員的值廣播到其他成員。 它是使用共用的變數值時提供這類共用的變數會很困難 （例如，在需要不同的變數，每個層級的遞迴函式） 的替代方案。 **Copyprivate**子句只能出現在**單一**指示詞。

語法**copyprivate**子句如下所示：

```

copyprivate(
variable-list
)

```

效果**copyprivate**其變數清單中的變數上的子句執行相關聯的結構化區塊之後，就會發生**單一**建構，以及之前的任何執行緒中小組尚餘屏障建構結尾。 然後，在小組中每個變數中的所有其他執行緒*變數清單*，該變數會變成 （如同依指派） 已定義的對應值的結構化執行建構的執行緒中的變數區塊。

若要限制**copyprivate**子句如下所示：

- 中指定的變數**copyprivate**子句不得出現在**私用**或是**firstprivate**子句相同**單一**指示詞。

- 如果**單一**指示詞搭配**copyprivate**子句發生在平行區域的動態範圍中，指定中的所有變數**copyprivate**子句必須是在封入內容中的私用。

- 中指定的變數**copyprivate**子句必須具有可存取模稜兩可的複製指派運算子。