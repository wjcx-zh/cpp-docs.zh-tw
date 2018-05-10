---
title: omp_set_dynamic |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_set_dynamic OpenMP function
ms.assetid: 3845faf2-a0ca-45a5-ae70-2a7a6164f1e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 18521113125eb49fa413568b6a62472bb50a7924
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="ompsetdynamic"></a>omp_set_dynamic
指出可以調整的執行階段的後續平行區域中的可用執行緒數目。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_dynamic(  
   int val  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `val`  
 值，指出是否可以調整執行階段的後續平行區域中的可用執行緒數目。  如果是非零值，執行階段可以調整執行緒數目，如果是零，執行階段就不會動態調整執行緒數目。  
  
## <a name="remarks"></a>備註  
 執行緒的數目將永遠不會超過所設定的值[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)。  
  
 使用[omp_get_dynamic](../../../parallel/openmp/reference/omp-get-dynamic.md)要顯示的目前設定`omp_set_dynamic`。  
  
 設定`omp_set_dynamic`會覆寫的設定[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)環境變數。  
  
 如需詳細資訊，請參閱[3.1.7 omp_set_dynamic 函式](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_set_dynamic.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main()   
{  
    omp_set_dynamic(9);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_dynamic( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_dynamic( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)