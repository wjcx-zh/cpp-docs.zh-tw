---
title: "A.23   Examples of the ordered Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: f8fa761b-7fc5-4447-95f9-8571e9ca31bf
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.23   Examples of the ordered Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

可以有多個已排序的區段與`for`指定具有`ordered`子句。  第一個範例中是不相容，因為 API 會指定下列：  
  
 "的迴圈反覆運算`for`建構必須不會執行相同`ordered`指示詞超過一次，而且它必須不會執行一個以上的`ordered`指示詞。" \(請參閱[一節 2.6.6](../../parallel/openmp/2-6-6-ordered-construct.md) 在頁面上 22\)  
  
 在此不相容的範例中，所有反覆項目會執行兩個已排序的區段：  
  
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
  
 下列標準的範例所示`for`具有多個已排序的區段：  
  
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