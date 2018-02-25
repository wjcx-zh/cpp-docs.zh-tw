---
title: omp_get_dynamic | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- omp_get_dynamic
dev_langs:
- C++
helpviewer_keywords:
- omp_get_dynamic OpenMP function
ms.assetid: efa843c5-7266-4a75-8db3-22992663d9db
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 865104055fc98946c09152f328f4812af0120e64
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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
  
## <a name="see-also"></a>請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)