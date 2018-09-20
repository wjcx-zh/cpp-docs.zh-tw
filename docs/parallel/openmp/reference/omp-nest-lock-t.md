---
title: omp_nest_lock_t |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- omp_nest_lock_t OpenMP data type
ms.assetid: fceac9fb-96d2-42b0-af19-c9b078380618
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b25a76332325247987751d8e9c41914da51f4a70
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46390129"
---
# <a name="ompnestlockt"></a>omp_nest_lock_t

保留鎖定的相關資訊的下列項目類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。

下列函式會使用**omp_nest_lock_t**:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)

- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)

- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)

- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)

- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

## <a name="example"></a>範例

請參閱[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)如需使用的範例**omp_nest_lock_t**。

## <a name="see-also"></a>另請參閱

[資料類型](../../../parallel/openmp/reference/openmp-data-types.md)