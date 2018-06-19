---
title: omp_destroy_nest_lock |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a01ff1b0e8b37a9bd8d380b6e0e59794412e51f8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33695014"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock
未初始化可巢狀的鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_destroy_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `lock`  
 類型的變數[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)初始化與[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)的使用範例`omp_destroy_nest_lock`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)