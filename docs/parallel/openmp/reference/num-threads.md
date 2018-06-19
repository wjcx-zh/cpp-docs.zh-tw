---
title: num_threads |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- num_threads
dev_langs:
- C++
helpviewer_keywords:
- num_threads OpenMP clause
ms.assetid: 09a56fc8-25c7-43e4-bbb5-71cb955d0b93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7dd57950d083c4f89ee2aa5962ad1e07a55a9a8
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33691882"
---
# <a name="numthreads"></a>num_threads
在執行緒小組設定執行緒的數目。  
  
## <a name="syntax"></a>語法  
  
```  
num_threads(num)  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `num`  
 執行緒的數目  
  
## <a name="remarks"></a>備註  
 `num_threads`子句具有與相同的功能[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函式。  
  
 `num_threads` 適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱[2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>範例  
 請參閱[平行](../../../parallel/openmp/reference/parallel.md)的使用範例`num_threads`子句。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)