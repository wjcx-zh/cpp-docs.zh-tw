---
title: "不可部分完成 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: atomic
dev_langs: C++
helpviewer_keywords: atomic OpenMP directive
ms.assetid: 275e0338-cf2f-4525-97b5-696250000df7
caps.latest.revision: "11"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1e3d190504a0e4caab864c637d7053836b01f88f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
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
  
## <a name="see-also"></a>請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)