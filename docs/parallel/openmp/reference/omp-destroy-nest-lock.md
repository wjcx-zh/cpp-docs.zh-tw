---
title: omp_destroy_nest_lock |Microsoft Docs
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
ms.openlocfilehash: 1d5cb4e985c82bec859959f374ffe35f33548228
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46377249"
---
# <a name="ompdestroynestlock"></a>omp_destroy_nest_lock

取消初始化可巢狀鎖定。

## <a name="syntax"></a>語法

```
void omp_destroy_nest_lock(
   omp_nest_lock_t *lock
);
```

### <a name="parameters"></a>參數

*lock*<br/>
類型的變數[omp_nest_lock_t](../../../parallel/openmp/reference/omp-nest-lock-t.md) ，初始化[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)。

## <a name="remarks"></a>備註

如需詳細資訊，請參閱 < [3.2.2 omp_destroy_lock 和 omp_destroy_nest_lock 函式](../../../parallel/openmp/3-2-2-omp-destroy-lock-and-omp-destroy-nest-lock-functions.md)。

## <a name="example"></a>範例

請參閱[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)如需使用的範例`omp_destroy_nest_lock`。

## <a name="see-also"></a>另請參閱

[函式](../../../parallel/openmp/reference/openmp-functions.md)