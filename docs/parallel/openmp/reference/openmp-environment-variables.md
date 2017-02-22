---
title: "OpenMP Environment Variables | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 2178ce2b-ffa1-45ec-a455-64437711d15d
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# OpenMP Environment Variables
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供用於 OpenMP API 的環境變數的連結。  
  
 Visual C\+\+ 實作標準 OpenMP 包括下列環境變數。  在程式啟動時讀取這些環境變數，並修改其值會在執行階段略過 \(比方說，使用[\_putenv、\_wputenv](../../../c-runtime-library/reference/putenv-wputenv.md)\)。  
  
|環境變數|描述|  
|----------|--------|  
|[OMP\_DYNAMIC](../../../parallel/openmp/reference/omp-dynamic.md)|指定執行階段 OpenMP 是否可以調整在平行區域中的執行緒數目。|  
|[OMP\_NESTED](../../../parallel/openmp/reference/omp-nested.md)|指定是否巢狀的平行處理原則已啟用，除非巢狀的平行處理原則已啟用或停用與`omp_set_nested`。|  
|[OMP\_NUM\_THREADS](../../../parallel/openmp/reference/omp-num-threads.md)|在平行區域中，設定執行緒的最大數目，除非藉由覆寫[omp\_set\_num\_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num\_threads](../../../parallel/openmp/reference/num-threads.md)。|  
|[OMP\_SCHEDULE](../../../parallel/openmp/reference/omp-schedule.md)|可修改[schedule](../../../parallel/openmp/reference/schedule.md)子句時`schedule(runtime)`中所指定`for`或`parallel for`指示詞。|  
  
## 請參閱  
 [Library Reference](../../../parallel/openmp/reference/openmp-library-reference.md)