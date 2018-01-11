---
title: "2.1 指示詞格式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 918b6445-d35e-4176-9565-b045be941b4d
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c3ff4e0078ffd086ce3b62d8927184188f0ebdd8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="21-directive-format"></a>2.1 指示詞格式
在文法正式指定 OpenMP 指示詞的語法[旓紵 C](../../parallel/openmp/c-openmp-c-and-cpp-grammar.md)，和非正式地，如下所示：  
  
```  
#pragma omp directive-name  [clause[ [,] clause]...] new-line  
```  
  
 每個指示詞開頭**#pragma omp**，以減少與其他 （非 OpenMP 或廠商延伸 OpenMP） 的 pragma 指示詞具有相同名稱發生衝突的可能性。 指示詞的其餘部分會遵循的慣例的編譯器指示詞的 C 和 c + + 標準。 特別是，使用空白字元之前和之後 **#** ，以及有時必須使用空白字元分隔指示詞中的字詞。 前置處理語彙基元遵循**#pragma omp**受限於巨集取代。  
  
 指示詞會區分大小寫。 在指示詞子句出現的順序並不重要。 如有需要受限於所列出的每個子句描述中的限制，可能會重複指示詞上的子句。 如果*變數清單*會出現在子句中，它必須指定只有變數。 只有一個*指示詞名稱*可以指定每個指示詞。  例如，不允許下列指示詞：  
  
```  
/* ERROR - multiple directive names not allowed */  
#pragma omp parallel barrier  
```  
  
 OpenMP 指示詞套用至最多一個後續陳述式，這必須是結構化的區塊。