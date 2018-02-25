---
title: "平行 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9293a70ce0615adf1e40bcb19b1706d9e39d4cca
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="parallel"></a>parallel
定義在平行區域，也就是將由多個執行緒以平行方式執行的程式碼。  
  
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
 零個或多個子句。  請參閱 < 備註 > 一節如需所支援的子句**平行**。  
  
## <a name="remarks"></a>備註  
 **平行**指示詞可支援下列 OpenMP 子句：  
  
-   [copyin](../../../parallel/openmp/reference/copyin.md)  
  
-   [default](../../../parallel/openmp/reference/default-openmp.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [if](../../../parallel/openmp/reference/if-openmp.md)  
  
-   [num_threads](../../../parallel/openmp/reference/num-threads.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
-   [reduction](../../../parallel/openmp/reference/reduction.md)  
  
-   [shared](../../../parallel/openmp/reference/shared-openmp.md)  
  
 **平行**也可用以[區段](../../../parallel/openmp/reference/sections-openmp.md)和[如](../../../parallel/openmp/reference/for-openmp.md)指示詞。  
  
 如需詳細資訊，請參閱[2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>範例  
 下列範例會示範如何設定的執行緒數目，並定義在平行區域。 根據預設，執行緒的數目等於在電腦上的邏輯處理器數目。 例如，如果您有一個已啟用超執行緒之實體處理器的機器，它將會有兩個邏輯處理器，因此，兩個執行緒。  
  
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
 請注意，在不同電腦上會有所不同之輸出的順序。  
  
## <a name="see-also"></a>請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)