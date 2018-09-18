---
title: omp_unset_lock |Microsoft Docs
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
ms.openlocfilehash: 6b0b7b796ce5db6cfe23eea3608db171ff38e263
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059054"
---
# <a name="ompunsetlock"></a>omp_unset_lock
釋放鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_unset_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>參數
  
*lock*<br/>
類型的變數[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) ，初始化[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)、 執行緒所擁有和函式中執行。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [3.2.4 omp_unset_lock 和 omp_unset_nest_lock 函式](../../../parallel/openmp/3-2-4-omp-unset-lock-and-omp-unset-nest-lock-functions.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)如需使用的範例`omp_unset_lock`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)