---
title: omp_set_num_threads |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
f1_keywords:
- omp_set_num_threads
dev_langs:
- C++
helpviewer_keywords:
- omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 849bdade5c6abfad07ebed262fb367487d3e1415
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047885"
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
在後續的平行區域，設定執行緒數目，但覆寫[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
### <a name="parameters"></a>參數
  
*num_threads*<br/>
在平行區域中的執行緒數目。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 < [3.1.1 omp_set_num_threads 函式](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)如需使用的範例`omp_set_num_threads`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)