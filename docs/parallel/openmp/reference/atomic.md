---
title: 不可部分完成 |Microsoft 文件
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
ms.openlocfilehash: bf6287ff3c44d508a3e4293340e652edb201282f
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33694403"
---
# <a name="atomic"></a>atomic
指定將自動更新的記憶體位置。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp atomic  
   expression  
```  
  
#### <a name="parameters"></a>參數  
 `expression`  
 您想要防止多個寫入包含其記憶體位置的左值的陳述式。 如需合法的運算式形式的詳細資訊，請參閱 OpenMP 規格。  
  
## <a name="remarks"></a>備註  
 `atomic`指示詞可支援不含 OpenMP 子句。  
  
 如需詳細資訊，請參閱[2.6.4 atomic 建構](../../../parallel/openmp/2-6-4-atomic-construct.md)。  
  
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