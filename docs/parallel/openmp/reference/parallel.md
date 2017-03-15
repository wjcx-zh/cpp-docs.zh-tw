---
title: "平行 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: 12
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 3168772cbb7e8127523bc2fc2da5cc9b4f59beb8
ms.openlocfilehash: 74bad2cbe60e7f03c39d243e380db5dea7430c28
ms.lasthandoff: 02/24/2017

---
# <a name="parallel"></a>parallel
定義一個平行區域，也就是將由多個執行緒，以平行方式執行的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `clause` (選擇性)  
 零個或多個子句。  請參閱 < 備註 > 一節的清單所支援的子句**平行**。  
  
## <a name="remarks"></a>備註  
 **平行**指示詞可支援下列 OpenMP 子句︰  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [如果](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [減少](../../../parallel/openmp/reference/reduction.md)  
  
-   [共用](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **平行**也可與[章節](../../../parallel/openmp/reference/sections-openmp.md)和[的](../../../parallel/openmp/reference/for-openmp.md)指示詞。  
  
 如需詳細資訊，請參閱[2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定執行緒數目，並定義一個平行區域。 根據預設，執行緒的數目等於電腦上的邏輯處理器的數目。 例如，如果您有一個已啟用超執行緒的實體處理器的電腦，它會有兩個邏輯處理器，因此，兩個執行緒。  
  
```  
// omp_parallel.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(4)  
   {  
      int i = omp_get_thread_num();  
      printf_s("Hello from thread %d\n", i);  
   }  
}  
```  
  
```Output  
Hello from thread 0  
Hello from thread 1  
Hello from thread 2  
Hello from thread 3  
```  
  
## <a name="comment"></a>註解  
 請注意不同輸出的順序時，可以在不同電腦上。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)
