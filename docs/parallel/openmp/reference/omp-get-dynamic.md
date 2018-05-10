---
title: omp_get_dynamic |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d97cae8091f88c283412b36ef757b03c72f7580d
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="ompgetdynamic"></a>omp_get_dynamic
傳回值，指出是否可以調整執行階段的後續平行區域中的可用執行緒數目。  
  
## <a name="syntax"></a>語法  
  
```  
int omp_get_dynamic();  
```  
  
## <a name="return-value"></a>傳回值  
 如果是非零值，則會啟用動態調整的執行緒。  
  
## <a name="remarks"></a>備註  
 使用指定的執行緒動態調整[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)和[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。  
  
 如需詳細資訊，請參閱[3.1.7 omp_set_dynamic 函式](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)的使用範例`omp_get_dynamic`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)