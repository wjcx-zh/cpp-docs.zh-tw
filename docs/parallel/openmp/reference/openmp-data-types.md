---
title: OpenMP 資料類型
ms.date: 10/23/2018
f1_keywords:
- OpenMP data types
- omp_lock_t
- omp_nest_lock_t
helpviewer_keywords:
- OpenMP data types
- omp_lock_t OpenMP data type
- omp_nest_lock_t OpenMP data type
ms.assetid: cf1e1045-4d12-4d03-80b7-d5843b80ef85
ms.openlocfilehash: bacb48194015f8fd6c80a9868af06702deceab6f
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50533766"
---
# <a name="openmp-data-types"></a>OpenMP 資料類型

提供在 OpenMP API 中使用的資料類型的連結。

Visual c + + 實作的 openmp 標準包含下列資料類型。

|資料類型|描述|
|---------|-----------|
|[omp_lock_t](#omp-lock-t)|保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。|
|[omp_nest_lock_t](#omp-nest-lock-t)|保留鎖定的相關資訊的下列項目之一的類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。|

## <a name="omp-lock-t"></a>omp_lock_t

保留鎖定，鎖定是否可供使用，或如果執行緒擁有鎖定的狀態類型。

下列函式會使用`omp_lock_t`:

- [omp_init_lock](openmp-functions.md#omp-init-lock)
- [omp_destroy_lock](openmp-functions.md#omp-destroy-lock)
- [omp_set_lock](openmp-functions.md#omp-set-lock)
- [omp_unset_lock](openmp-functions.md#omp-unset-lock)
- [omp_test_lock](openmp-functions.md#omp-test-lock)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_lock](openmp-functions.md#omp-init-lock)如需使用的範例`omp_lock_t`。

## <a name="omp-nest-lock-t"></a>omp_nest_lock_t

保留鎖定的相關資訊的下列項目類型： 是否鎖定可供使用，以及執行緒的識別擁有鎖定，並將巢狀的計數。

下列函式會使用`omp_nest_lock_t`:

- [omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)
- [omp_destroy_nest_lock](openmp-functions.md#omp-destroy-nest-lock)
- [omp_set_nest_lock](openmp-functions.md#omp-set-nest-lock)
- [omp_unset_nest_lock](openmp-functions.md#omp-unset-nest-lock)
- [omp_test_nest_lock](openmp-functions.md#omp-test-nest-lock)

如需詳細資訊，請參閱 < [3.2 鎖定函式](../../../parallel/openmp/3-2-lock-functions.md)。

### <a name="example"></a>範例

請參閱[omp_init_nest_lock](openmp-functions.md#omp-init-nest-lock)如需使用的範例`omp_nest_lock_t`。
