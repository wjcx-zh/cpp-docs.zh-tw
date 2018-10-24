---
title: OpenMP 資料類型 |Microsoft Docs
ms.custom: ''
ms.date: 10/23/2018
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
dev_langs:
- C++
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 254dffebc258867088f738b10a11bf48d31bd0a4
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2018
ms.locfileid: "49990059"
---
# <a name="openmp-data-types"></a>OpenMP 資料類型

提供在 OpenMP API 中使用的資料類型的連結。

Visual c + + 實作的 openmp 標準包含下列資料類型。

資料類型                           | 描述
----------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[omp_lock_t](#omp-lock-t)           | 保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。
[omp_nest_lock_t](#omp-nest-lock-t) | 保留鎖定的相關資訊的下列項目之一的類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。

## <a name="omp-lock-t"></a>omp_lock_t

保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。

下列函式會使用`omp_lock_t`:

- [omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)
- [omp_destroy_lock](../../../parallel/openmp/reference/omp-destroy-lock.md)
- [omp_set_lock](../../../parallel/openmp/reference/omp-set-lock.md)
- [omp_unset_lock](../../../parallel/openmp/reference/omp-unset-lock.md)
- [omp_test_lock](../../../parallel/openmp/reference/omp-test-lock.md)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_lock](../../../parallel/openmp/reference/omp-init-lock.md)如需使用的範例`omp_lock_t`。

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

保留鎖定的相關資訊的下列項目類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。

下列函式會使用`omp_nest_lock_t`:

- [omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)
- [omp_destroy_nest_lock](../../../parallel/openmp/reference/omp-destroy-nest-lock.md)
- [omp_set_nest_lock](../../../parallel/openmp/reference/omp-set-nest-lock.md)
- [omp_unset_nest_lock](../../../parallel/openmp/reference/omp-unset-nest-lock.md)
- [omp_test_nest_lock](../../../parallel/openmp/reference/omp-test-nest-lock.md)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_nest_lock](../../../parallel/openmp/reference/omp-init-nest-lock.md)如需使用的範例`omp_nest_lock_t`。
