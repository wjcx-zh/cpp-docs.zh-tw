---
title: "2.6.3 barrier 指示詞 |Microsoft 文件"
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
ms.assetid: 4485a3d7-533f-4fec-8128-a131bec7fa16
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d9c64787d9c6cc2dd0809f75f8f9db9819174d0f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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