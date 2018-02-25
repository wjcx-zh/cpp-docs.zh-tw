---
title: omp_set_nest_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_set_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_set_nest_lock OpenMP function
ms.assetid: b98ed889-ff8e-4217-a3e9-3993ed8699af
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f2ae23cfd58b55881ebaa25f55d121d7ab45f3b3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
---
# <a name="ompsetnestlock"></a>omp_set_nest_lock
區塊執行緒執行，直到鎖定可用為止。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_nest_lock(  
   omp_nest_lock_t *lock  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `lock`  
 類型的變數[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md)初始化與[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[3.2.3 omp_set_lock 和 omp_set_nest_lock 函式](../../../parallel/openmp/3-2-3-omp-set-lock-and-omp-set-nest-lock-functions.md)。  
  
## <a name="examples"></a>範例  
 請參閱[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)的使用範例`omp_set_nest_lock`。  
  
## <a name="see-also"></a>請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)