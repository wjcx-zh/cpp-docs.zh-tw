---
title: "OpenMP 環境變數 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: e285ab34c7bf993b919a2c917f44828c21970f67
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-environment-variables"></a>OpenMP 環境變數
提供連結 OpenMP API 中使用的環境變數。  
  
 OpenMP 標準的 Visual c + + 實作會包含下列環境變數。 這些環境變數會在程式啟動時讀取，並修改其值的結果會忽略在執行階段 (例如，使用[_putenv、 _wputenv](../../../c-runtime-library/reference/putenv-wputenv.md))。  
  
|環境變數|描述|  
|--------------------------|-----------------|  
|[OMP_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|指定執行階段 OpenMP 是否可調整的平行區域中的執行緒數目。|  
|[OMP_NESTED](../../../parallel/openmp/reference/omp-nested.md)|指定是否巢狀平行處理原則已啟用，除非啟用或停用巢狀平行處理原則`omp_set_nested`。|  
|[OMP_NUM_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|在平行區域中，設定執行緒的數目上限，除非被[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](../../../parallel/openmp/reference/num-threads.md)。|  
|[OMP_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|可修改[排程](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中指定`for`或`parallel for`指示詞。|  
  
## <a name="see-also"></a>請參閱  
 [程式庫參考](../../../parallel/openmp/reference/openmp-library-reference.md)