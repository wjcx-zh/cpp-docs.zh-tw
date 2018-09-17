---
title: 平行 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- parallel
dev_langs:
- C++
helpviewer_keywords:
- parallel OpenMP directive
ms.assetid: b8e90073-e85b-4d39-8ed8-0364441794fb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1c8b1466eae343b6c644b6ecfbd919c3241259bf
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45705961"
---
# <a name="parallel"></a>parallel
定義在平行區域，也就是將多個執行緒以平行方式執行的程式碼。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp parallel [clauses]  
{  
   code_block  
}  
```  
  
## <a name="arguments"></a>引數

*子句*<br/>
（選擇性）零個或多個子句。  請參閱所支援的子句清單的 < 備註 > 一節**平行**。  
  
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
  
 **平行**也可與[章節](../../../parallel/openmp/reference/sections-openmp.md)並[如](../../../parallel/openmp/reference/for-openmp.md)指示詞。  
  
 如需詳細資訊，請參閱 < [2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>範例  
 下列範例示範如何設定的執行緒數目，以及定義在平行區域。 根據預設，執行緒數目等於電腦上的邏輯處理器的數目。 例如，如果您有已啟用超執行緒的一個實體處理器的電腦時，它會有兩個邏輯處理器，因此，兩個執行緒。  
  
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
 請注意，在不同電腦而異之輸出的順序。  
  
## <a name="see-also"></a>另請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)