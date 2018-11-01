---
title: 2.1 指示詞格式
ms.date: 11/04/2016
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
ms.openlocfilehash: 6ee977005d421a59e71f852be3d78a2caad9b45b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629485"
---
# <a name="21-directive-format"></a>2.1 指示詞格式

OpenMP 指示詞的語法正式指定文法[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)，和非正式地，如下所示：

```
#pragma omp directive-name  [clause[ [,] clause]...] new-line
```

每個指示詞開頭 **#pragma omp**，以降低與具有相同名稱的其他 （非 OpenMP 或廠商延伸模組與 OpenMP） pragma 指示詞衝突的可能性。 指示詞的其餘部分會遵循的編譯器指示詞的 C 和 c + + 標準的慣例。 特別是，使用空白字元之前和之後**#**，和有時也泛空白字元必須用來分隔指示詞中的文字。 前置處理語彙基元 **#pragma omp**限於巨集取代。

指示詞會區分大小寫。 指示詞中子句出現的順序並不重要。 如有需要受限於每個子句描述中所列的限制，可能會重複上指示詞子句。 如果*變數清單*會出現在子句中，它必須指定只有變數。 只有一個*指示詞名稱*可以指定每個指示詞。  比方說，不允許下列指示詞：

```
/* ERROR - multiple directive names not allowed */
#pragma omp parallel barrier
```

OpenMP 指示詞套用至最多一個後續陳述式，它必須是結構化的區塊。