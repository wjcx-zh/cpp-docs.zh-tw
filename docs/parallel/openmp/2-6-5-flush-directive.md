---
title: 2.6.5 flush 指示詞
ms.date: 11/04/2016
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
ms.openlocfilehash: 7aca747a3d9645be4f9888b072127dc3040280fb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660079"
---
# <a name="265-flush-directive"></a>2.6.5 flush 指示詞

**排清**指示詞，明確或隱含的是否指定的實作，才能確保小組中的所有執行緒都有一致的檢視 （下方） 中指定特定物件的 「 跨執行緒 「 序列點記憶體。 這表示先前評估的運算式參考那些物件都已完成，而且還沒有開始後續評估。 比方說，編譯器必須從暫存器物件的值還原記憶體中，並且硬體可能需要排清寫入緩衝區記憶體並重新載入記憶體中物件的值。

語法**排清**指示詞時，如下所示：

```
#pragma omp flush [(variable-list)]  new-line
```

如果需要同步處理的物件可以所有指定的變數，則這些變數可以指定選擇性*變數清單*。 指標是否存在於*變數清單*，指標本身會排清，不是物件指標參考。

A**排清**指示詞，而不需要*變數清單*同步所有共用的物件，但無法存取的物件不具有自動儲存期。 (這是可能會有更多的額外負荷比**排清**具有*變數清單*。)A**排清**指示詞，而不需要*變數清單*隱含的下列指示詞：

- `barrier`

- 在進入和結束從**重要**

- 在進入和結束 `ordered`

- 在進入和結束從**平行**

- 在結束**的**

- 在結束**區段**

- 在結束**單一**

- 在進入和結束從**的平行處理**

- 在進入和結束從**平行處理區段**

如果不隱含的指示詞`nowait`出現子句時。 請注意，**排清**指示詞不隱含的下列其中一項：

- 在進入**的**

- 在進入或結束**master**

- 在進入**區段**

- 在進入**單一**

存取具有 volatile 限定類型之物件的值參考行為好像**排清**指示詞指定該物件在前一個序列點。 修改 volatile 限定類型之物件的值參考行為好像**排清**指示詞指定該物件在後續的序列點。

請注意，因為**排清**指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，它在程式內的位置上。 請參閱[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式文法。 下列範例會說明這些限制。

```
/* ERROR - The flush directive cannot be the immediate
*          substatement of an if statement.
*/
if (x!=0)
   #pragma omp flush (x)
...

/* OK - The flush directive is enclosed in a
*      compound statement
*/
if (x!=0) {
   #pragma omp flush (x)
}
```

若要限制**排清**指示詞如下所示：

- 中指定的變數**排清**指示詞不能是參考型別。