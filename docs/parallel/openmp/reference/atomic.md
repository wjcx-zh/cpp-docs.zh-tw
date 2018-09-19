---
title: 不可部分完成 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- atomic
dev_langs:
- C++
helpviewer_keywords:
- atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7e9e9ecad2f6ea53e2f922799340eee47dd4a7e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46037485"
---
# <a name="atomic"></a>atomic
指定的記憶體位置會以不可分割方式更新。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>參數  
*運算式*<br/>
您想要防止多個寫入包含其記憶體位置的左值的陳述式。 如需有關 form 合法的運算式的詳細資訊，請參閱的 OpenMP 規格。  
  
## <a name="remarks"></a>備註  
 `atomic`指示詞可支援無 OpenMP 子句。  
  
 如需詳細資訊，請參閱 < [2.6.4 atomic 建構](../../../parallel/openmp/2-6-4-atomic-construct.md)。  
  
## <a name="example"></a>範例  
  
```  
// omp_atomic.cpp  
// compile with: /openmp   
#include <stdio.h>  
#include <omp.h>  
  
#define MAX 10  
  
int main() {  
   int count = 0;  
   #pragma omp parallel num_threads(MAX)  
   {  
      #pragma omp atomic  
      count++;  
   }  
   printf_s("Number of threads: %d\n", count);  
}  
```  
  
```Output  
Number of threads: 10  
```  
  
## <a name="see-also"></a>另請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)