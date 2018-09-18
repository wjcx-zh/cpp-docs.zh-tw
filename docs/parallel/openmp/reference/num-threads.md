---
title: num_threads |Microsoft Docs
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
ms.openlocfilehash: d3485d534cf279863b241abcd26195cdde7fea19
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46016282"
---
# <a name="numthreads"></a>num_threads
在執行緒小組設定執行緒的數目。  
  
## <a name="syntax"></a>語法  
  
```  
num_threads(num)  
```  
  
### <a name="parameters"></a>參數
  
*num*<br/>
執行緒數目  
  
## <a name="remarks"></a>備註  
 `num_threads`子句具有與相同的功能[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函式。  
  
 `num_threads` 適用於下列指示詞：  
  
-   [parallel](../../../parallel/openmp/reference/parallel.md)  
  
-   [for](../../../parallel/openmp/reference/for-openmp.md)  
  
-   [區段](../../../parallel/openmp/reference/sections-openmp.md)  
  
 如需詳細資訊，請參閱 < [2.3 parallel 建構](../../../parallel/openmp/2-3-parallel-construct.md)。  
  
## <a name="example"></a>範例  
 請參閱[平行](../../../parallel/openmp/reference/parallel.md)如需使用的範例`num_threads`子句。  
  
## <a name="see-also"></a>另請參閱  
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)