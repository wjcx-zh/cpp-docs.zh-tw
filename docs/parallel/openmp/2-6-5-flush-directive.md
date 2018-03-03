---
title: "2.6.5 flush 指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: a2ec5f74-9c37-424a-8376-47ab4a5829a2
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 7607070692941606b863be9248b2d69f093f3a13
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="265-flush-directive"></a>2.6.5 flush 指示詞
**排清**指示詞，是否明確或隱含的請指定"跨執行緒 「 序列點的實作，才能確保小組中的所有執行緒都有一致 （下方） 中指定特定物件的檢視記憶體。 這表示上一個評估的運算式參考那些物件都已完成，而且還沒有開始後續評估。 例如，編譯器必須從暫存器物件的值還原記憶體中，並且硬體可能需要排清寫入緩衝區的記憶體，並重新載入記憶體中物件的值。  
  
 語法**排清**指示詞時，如下所示：  
  
```  
#pragma omp flush [(variable-list)]  new-line  
```  
  
 如果需要同步處理的物件，即可所有指定的變數，則您可以指定那些變數中選擇性*變數清單*。 如果指標位於*變數清單*，指標本身會排清，不是物件指標參考。  
  
 A**排清**指示詞沒有*變數清單*有自動儲存期，所有共用的物件，但無法存取的物件不會同步處理。 (這是可能有更多成本負擔比**排清**與*變數清單*。)A**排清**指示詞沒有*變數清單*隱含的下列指示詞：  
  
-   `barrier`  
  
-   在進入和結束**重大**  
  
-   在進入和結束`ordered`  
  
-   在進入和結束**平行**  
  
-   在結束**的**  
  
-   在結束**區段**  
  
-   在結束**單一**  
  
-   在進入和結束**平行的**  
  
-   在進入和結束**平行區段**  
  
 如果指示詞都沒有隱含`nowait`子句。 請注意，**排清**指示詞沒有隱含的下列其中一項：  
  
-   在進入**的**  
  
-   在項目或從結束**master**  
  
-   在進入**區段**  
  
-   在進入**單一**  
  
 存取具有 volatile 限定類型物件的值參考行為會如同沒有**排清**指示詞指定的物件，在前一個序列點。 修改的物件具有 volatile 限定類型的值參考行為會如同沒有**排清**指示詞指定該物件在後續的序列點。  
  
 請注意，因為**排清**指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，在程式中的位置。 請參閱[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式文法。 下列範例會示範這些限制。  
  
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
  
 若要限制**排清**指示詞如下：  
  
-   中指定的變數**排清**指示詞不能參考型別。