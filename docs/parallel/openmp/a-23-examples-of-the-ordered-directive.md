---
title: 已排序的指示詞 A.23 範例 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 37cc4ea9db8cbd1a7bf095e2bde0ae482053a584
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="a23---examples-of-the-ordered-directive"></a>A.23 ordered 指示詞範例
它是可以有多個已排序的區段，並有`for`指定與`ordered`子句。 第一個範例是不相容，因為下列 API 會指定：  
  
 「 使用迴圈的反覆項目`for`建構必須執行相同`ordered`指示詞超過一次，而且只能執行一個以上的`ordered`指示詞。 」 (請參閱[區段 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md)在頁面上 22)  
  
 在此不相容的範例中，所有的反覆項目執行 2 的已排序的區段：  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
    #pragma omp ordered  
    { ... }  
    ...  
}  
```  
  
 下列標準範例所示`for`具有多個排序區段：  
  
```  
#pragma omp for ordered  
for (i=0; i<n; i++)   
{  
    ...  
    if (i <= 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
    (i > 10)   
    {  
        ...  
        #pragma omp ordered  
        { ... }  
    }  
    ...  
}  
```