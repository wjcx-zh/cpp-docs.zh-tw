---
title: omp_destroy_nest_lock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_destroy_nest_lock
dev_langs:
- C++
helpviewer_keywords:
- omp_destroy_nest_lock OpenMP function
ms.assetid: 0ab1352b-668f-43dd-b441-31ec4cc53e68
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f7c62ba49f98581c233966dd8d7d71bb3433ae3f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)