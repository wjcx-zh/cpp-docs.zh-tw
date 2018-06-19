---
title: omp_set_nested |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nested OpenMP function
ms.assetid: fa1cb08c-7b8b-42c9-8654-2c33dcffb5b6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b6539167b936efdc4c9f407cd951c9c582b0a138
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33692177"
---
# <a name="ompsetnested"></a>omp_set_nested
啟用巢狀平行處理原則。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_nested(  
   int val  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `val`  
 如果是非零值，可讓巢狀平行處理原則。 如果是零，會停用巢狀平行處理原則。  
  
## <a name="remarks"></a>備註  
 OMP 巢狀平行處理原則可以與開啟`omp_set_nested`，或藉由設定[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)環境變數。  
  
 設定`omp_set_nested`會覆寫的設定`OMP_NESTED`環境變數。  
  
 啟用時，環境變數可以中斷否則操作的程式，因為執行緒的數目以指數方式增加巢狀平行區域時。  例如 6 次與 OMP 設為 4 的執行緒數目進行遞迴需要 4096 (4，6 冪) 的函式的執行緒在一般情況下，應用程式的效能會降低，如果執行緒數目超過處理器的數目。 I/O 繫結的應用程式是一個例外狀況。  
  
 使用[omp_get_nested](../../../parallel/openmp/reference/omp-get-nested.md)要顯示的目前設定`omp_set_nested`。  
  
 如需詳細資訊，請參閱[3.1.9 omp_set_nested 函式](../../../parallel/openmp/3-1-9-omp-set-nested-function.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_set_nested.cpp  
// compile with: /openmp  
#include <stdio.h>  
#include <omp.h>  
  
int main( )   
{  
    omp_set_nested(1);  
    omp_set_num_threads(4);  
    printf_s("%d\n", omp_get_nested( ));  
    #pragma omp parallel  
        #pragma omp master  
        {  
            printf_s("%d\n", omp_get_nested( ));  
        }  
}  
```  
  
```Output  
1  
1  
```  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)