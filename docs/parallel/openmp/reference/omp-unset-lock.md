---
title: omp_unset_lock |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_unset_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_unset_lock OpenMP function
ms.assetid: 68fcb728-040b-4bad-979e-aaecb9097a4e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 243ff6d2336d3e293d009f82ba4a39243e076f94
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="ompunsetlock"></a>omp_unset_lock
釋放鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `lock`  
 類型的變數[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md)初始化與[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)、 執行緒所擁有和函式中執行。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)的使用範例`omp_unset_lock`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)