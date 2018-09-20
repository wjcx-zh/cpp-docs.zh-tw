---
title: omp_lock_t |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_lock_t
dev_langs:
- C++
helpviewer_keywords:
- omp_lock_t OpenMP data type
ms.assetid: 51b80629-4ffc-4b8a-95c7-1af048f1f286
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f109ae179c1fcb3393a41d6c0831b0faf69b1d77
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46444225"
---
# <a name="omplockt"></a>omp_lock_t

保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。

下列函式會使用**omp_lock_t**:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)

- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)

- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)

- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)

- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

## <a name="example"></a>範例

請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)如需使用的範例**omp_lock_t**。

## <a name="see-also"></a>另請參閱

[資料類型](../../../parallel/openmp/reference/openmp-data-types.md)