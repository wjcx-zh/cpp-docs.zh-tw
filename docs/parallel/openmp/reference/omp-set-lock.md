---
title: omp_set_lock |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_lock OpenMP function
ms.assetid: ded839cb-ca19-403f-8622-eb52ce512d31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 390090b0f4bf5f8795373db9f61f8365257ee95b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024903"
---
# <a name="ompsetlock"></a>omp_set_lock
封鎖執行緒執行，直到鎖定可用為止。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>參數
  
*lock*<br/>
類型的變數[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) ，初始化[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [3.2.3 omp_set_lock 和 omp_set_nest_lock 函式](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。  
  
## <a name="examples"></a>範例  
 請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)如需使用的範例`omp_set_lock`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)