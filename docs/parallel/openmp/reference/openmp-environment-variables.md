---
title: OpenMP 環境變數 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 98b61535fd07066c4a1ee24658fdfe81047efc90
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446565"
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數

提供連結 OpenMP API 中使用的環境變數。

Visual c + + 實作的 openmp 標準包含下列環境變數。 這些環境變數會在程式啟動時讀取和修改其值會被忽略，在執行階段 (例如，使用[_putenv、 _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。

|環境變數|描述|
|--------------------------|-----------------|
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|指定執行階段的 OpenMP 是否可調整的平行區域中的執行緒數目。|
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|指定是否巢狀平行處理原則已啟用，除非已啟用或停用巢狀平行處理原則`omp_set_nested`。|
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|在平行區域中，設定執行緒數目上限，但覆寫[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或是[num_threads](../../../parallel/openmp/reference/num-threads.md)。|
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|修改的行為[排程](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。|

## <a name="see-also"></a>另請參閱

[程式庫參考](../../../parallel/openmp/reference/openmp-library-reference.md)