---
title: omp_get_dynamic |Microsoft Docs
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
ms.openlocfilehash: c2b5a285ef019cd1752b60065f7040d9a937ce38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46389885"
---
# <a name="ompgetdynamic"></a>omp_get_dynamic

傳回值，這個值，指出是否可以調整執行階段在後續的平行區域中可用的執行緒數目。

## <a name="syntax"></a>語法

```
int omp_get_dynamic();
```

## <a name="return-value"></a>傳回值

如果是非零值，則會啟用動態調整的執行緒。

## <a name="remarks"></a>備註

使用指定的執行緒的動態調整[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)並[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)。

如需詳細資訊，請參閱 < [3.1.7 omp_set_dynamic 函式](../../../parallel/openmp/3-1-7-omp-set-dynamic-function.md)。

## <a name="example"></a>範例

請參閱[omp_set_dynamic](../../../parallel/openmp/reference/omp-set-dynamic.md)如需使用的範例`omp_get_dynamic`。

## <a name="see-also"></a>另請參閱

[函式](../../../parallel/openmp/reference/openmp-functions.md)