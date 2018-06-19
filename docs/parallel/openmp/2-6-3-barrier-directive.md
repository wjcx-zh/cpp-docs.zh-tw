---
title: 2.6.3 barrier 指示詞 |Microsoft 文件
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
ms.openlocfilehash: 68df92207feb45a77055098cdb1227a68b04bcab
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33689788"
---
# <a name="263-barrier-directive"></a>2.6.3 barrier 指示詞
**屏障**指示詞會同步處理在小組中的所有執行緒。 當遇到，小組中的每個執行緒會等到所有其他已經達到這個點為止。 語法**屏障**指示詞時，如下所示：  
  
```  
#pragma omp barrier new-line  
```  
  
 在小組中的所有執行緒都遇到屏障之後，小組中的每個執行緒會開始之後 barrier 指示詞，以平行方式執行的陳述式。 請注意，因為**屏障**指示詞沒有 C 語言陳述式，其語法的一部分，有一些限制，在程式中的位置。 請參閱[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)正式文法。 下列範例會示範這些限制。  
  
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