---
title: 重要 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Critical
dev_langs:
- C++
helpviewer_keywords:
- critical OpenMP directive
ms.assetid: 2ab87d6d-5ca4-43ae-9f0a-1f517a6a2bab
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 90638ad00f120e23e4c9168710d1e099c2c74d09
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716946"
---
# <a name="critical"></a>critical
指定程式碼只執行一個執行緒上一次。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp critical [(name)]  
{  
   code_block  
}  
```  
  
## <a name="arguments"></a>引數

*name*<br/>
（選擇性）要找出重要的程式碼的名稱。 請注意，該名稱必須括在括號。  
  
## <a name="remarks"></a>備註  
 **重要**指示詞可支援無 OpenMP 子句。  
  
 如需詳細資訊，請參閱 < [2.6.2 重要建構](../../../parallel/openmp/2-6-2-critical-construct.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_critical.cpp  
// compile with: /openmp   
#include <omp.h>  
#include <stdio.h>  
#include <stdlib.h>  
  
#define SIZE 10  
  
int main()   
{  
    int i;  
    int max;  
    int a[SIZE];  
  
    for (i = 0; i < SIZE; i++)   
    {  
        a[i] = rand();  
        printf_s("%d\n", a[i]);  
    }  
  
    max = a[0];  
    #pragma omp parallel for num_threads(4)  
        for (i = 1; i < SIZE; i++)   
        {  
            if (a[i] > max)  
            {  
                #pragma omp critical  
                {  
                    // compare a[i] and max again because max   
                    // could have been changed by another thread after   
                    // the comparison outside the critical section  
                    if (a[i] > max)  
                        max = a[i];  
                }  
            }  
        }  
  
    printf_s("max = %d\n", max);  
}  
```  
  
```Output  
41  
18467  
6334  
26500  
19169  
15724  
11478  
29358  
26962  
24464  
max = 29358  
```  
  
## <a name="see-also"></a>另請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)