---
title: omp_get_nested |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_get_nested
dev_langs:
- C++
helpviewer_keywords:
- omp_get_nested OpenMP function
ms.assetid: e9784847-516e-40d3-89f7-b8b6898d8667
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20a7378ba7e7f6dcec55cfe265dd0873bdc1fd38
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46371949"
---
# <a name="ompgetnested"></a>omp_get_nested

傳回值，這個值，指出是否已啟用巢狀平行處理原則。

## <a name="syntax"></a>語法

```
int omp_get_nested( );
```

## <a name="return-value"></a>傳回值

如果是非零值，則會啟用巢狀平行處理原則。

## <a name="remarks"></a>備註

指定巢狀平行處理原則[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)並[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)。

如需詳細資訊，請參閱 < [3.1.10 omp_get_nested 函式](../../../parallel/openmp/3-1-10-omp-get-nested-function.md)。

## <a name="example"></a>範例

請參閱[omp_set_nested](../../../parallel/openmp/reference/omp-set-nested.md)如需使用的範例`omp_get_nested`。

## <a name="see-also"></a>另請參閱

[函式](../../../parallel/openmp/reference/openmp-functions.md)