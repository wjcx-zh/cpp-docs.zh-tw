---
title: "單一 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- Single
dev_langs:
- C++
helpviewer_keywords:
- single OpenMP directive
ms.assetid: 85cf94fb-cb9c-4d82-8609-adffa9f552e1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b93480f01ea35129812b3d4f3c42ce2130046243
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="single"></a>single
可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp single [clauses]   
{  
   code_block   
}  
```  
  
#### <a name="parameters"></a>參數  
 `clause` (選擇性)  
 零個或多個子句。 請參閱 < 備註 > 一節如需所支援的子句**單一**。  
  
## <a name="remarks"></a>備註  
 **單一**指示詞可支援下列 OpenMP 子句：  
  
-   [copyprivate](../../../parallel/openmp/reference/copyprivate.md)  
  
-   [firstprivate](../../../parallel/openmp/reference/firstprivate.md)  
  
-   [nowait](../../../parallel/openmp/reference/nowait.md)  
  
-   [private](../../../parallel/openmp/reference/private-openmp.md)  
  
 [主要](../../../parallel/openmp/reference/master.md)指示詞可讓您指定的一段程式碼應該只能在執行主要執行緒。  
  
 如需詳細資訊，請參閱[2.4.3 單一建構](../../../parallel/openmp/2-4-3-single-construct.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_single.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
int main() {  
   #pragma omp parallel num_threads(2)  
   {  
      #pragma omp single  
      // Only a single thread can read the input.  
      printf_s("read input\n");  
  
      // Multiple threads in the team compute the results.  
      printf_s("compute results\n");  
  
      #pragma omp single  
      // Only a single thread can write the output.  
      printf_s("write output\n");  
    }  
}  
```  
  
```Output  
read input  
compute results  
compute results  
write output  
```  
  
## <a name="see-also"></a>請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)