---
title: 使用 threadprivate 指示詞 A.26 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 6eda76c2-c4f1-4208-a900-e0ea98a53eca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7b74325ec96702838aaaf9be62d398178c8c2902
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690526"
---
# <a name="a26---using-the-threadprivate-directive"></a>A.26 使用 threadprivate 指示詞
下列範例示範如何使用`threadprivate`指示詞 ([區段 2.7.1](../../parallel/openmp/2-7-1-threadprivate-directive.md) 23 頁面上) 的個別計數器提供每個執行緒。  
  
 **範例 1：**  
  
```  
int counter = 0;  
#pragma omp threadprivate(counter)  
  
int sub()  
{  
    counter++;  
    return(counter);  
}  
```  
  
 **範例 2：**  
  
```  
int sub()  
{  
    static int counter = 0;  
    #pragma omp threadprivate(counter)  
    counter++;  
    return(counter);  
}  
```