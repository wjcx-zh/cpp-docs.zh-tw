---
title: 2.6.3 barrier 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8654534143e6feed06e93406c8fe03983ee9c2fc
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46429145"
---
# <a name="263-barrier-directive"></a>2.6.3 barrier 指示詞

**屏障**指示詞會在一個小組中的所有執行緒同步都處理。 遇到時，在小組中的每個執行緒會等候直到所有的其他人已經達到這個點為止。 語法**屏障**指示詞時，如下所示：

```
#pragma omp barrier new-line
```

在小組中的所有執行緒都遇到屏障之後，在小組中的每個執行緒就會開始之後 barrier 指示詞，以平行方式執行的陳述式。 請注意，因為**屏障**指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，它在程式內的位置上。 請參閱[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式文法。 下列範例會說明這些限制。

```
/* ERROR - The barrier directive cannot be the immediate
*          substatement of an if statement
*/
if (x!=0)
   #pragma omp barrier
...

/* OK - The barrier directive is enclosed in a
*      compound statement.
*/
if (x!=0) {
   #pragma omp barrier
}
```