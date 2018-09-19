---
title: omp_destroy_lock |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_destroy_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_lock OpenMP function
ms.assetid: b73ab036-b76f-4e42-82ff-c89db2edf7c0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5c24f09bbad550633c68c403c89362a293265111
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46019915"
---
# <a name="ompdestroylock"></a>omp_destroy_lock
未初始化的鎖定。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_destroy_lock(  
   omp_lock_t *lock  
);  
```  
  
### <a name="parameters"></a>參數
  
*lock*<br/>
類型的變數[omp_lock_t](../../../parallel/openmp/reference/omp-lock-t.md) ，初始化[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)如需使用的範例`omp_destroy_lock`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)