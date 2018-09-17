---
title: 排清 (OpenMP) |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- Flush
dev_langs:
- C++
helpviewer_keywords:
- flush OpenMP directive
ms.assetid: 150ca46e-d4f7-4423-b0a4-838df40aeb67
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ea89d4feb7a554c2495c11aa8acaeeaa8bc775f
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722055"
---
# <a name="flush-openmp"></a>flush (OpenMP)
指定所有執行緒都有相同的檢視，所有的共用物件的記憶體。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp flush [(var)]  
```  
  
## <a name="arguments"></a>引數

*var*<br/>
（選擇性）代表您想要同步處理的物件變數的逗號分隔清單。 如果`var`未指定，會在排清所有記憶體。  
  
## <a name="remarks"></a>備註  
 **排清**指示詞可支援無 OpenMP 子句。  
  
 如需詳細資訊，請參閱 < [2.6.5 flush 指示詞](../../../parallel/openmp/2-6-5-flush-directive.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_flush.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
void read(int *data) {  
   printf_s("read data\n");  
   *data = 1;  
}  
  
void process(int *data) {  
   printf_s("process data\n");  
   (*data)++;  
}  
  
int main() {  
   int data;  
   int flag;  
  
   flag = 0;  
  
   #pragma omp parallel sections num_threads(2)  
   {  
      #pragma omp section  
      {  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         read(&data);  
         #pragma omp flush(data)  
         flag = 1;  
         #pragma omp flush(flag)  
         // Do more work.  
      }  
  
      #pragma omp section   
      {  
         while (!flag) {  
            #pragma omp flush(flag)  
         }  
         #pragma omp flush(data)  
  
         printf_s("Thread %d: ", omp_get_thread_num( ));  
         process(&data);  
         printf_s("data = %d\n", data);  
      }  
   }  
}  
```  
  
```Output  
Thread 0: read data  
Thread 1: process data  
data = 2  
```  
  
## <a name="see-also"></a>另請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)