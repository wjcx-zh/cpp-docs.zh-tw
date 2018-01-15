---
title: "OMP_NUM_THREADS |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: OMP_NUM_THREADS
dev_langs: C++
helpviewer_keywords: OMP_NUM_THREADS OpenMP environment variable
ms.assetid: 4b558124-1387-4c30-a6a5-ff5345a9ced6
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a5f6af2ff547ddb95b6d4ef6b9c6d353399c17c5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ompnumthreads"></a>OMP_NUM_THREADS
在平行區域中，設定執行緒的數目上限，除非被[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)或[num_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
## <a name="syntax"></a>語法  
  
```  
set OMP_NUM_THREADS[=num]  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `num`  
 您想要在平行區域中，最多 64 Visual c + + 實作中的執行緒最大數目。  
  
## <a name="remarks"></a>備註  
 **OMP_NUM_THREADS**環境變數可以覆寫[omp_set_num_threads](../../../parallel/openmp/reference/omp-set-num-threads.md)函式或由[num_threads](../../../parallel/openmp/reference/num-threads.md)。  
  
 預設值`num`Visual c + + OpenMP 標準的實作是虛擬處理器數目，包括超執行緒的 Cpu。  
  
 如需詳細資訊，請參閱[4.2 OMP_NUM_THREADS](../../../parallel/openmp/4-2-omp-num-threads.md)。  
  
## <a name="example"></a>範例  
 下列命令**OMP_NUM_THREADS**為 16 的環境變數：  
  
```  
set OMP_NUM_THREADS=16  
```  
  
 下列命令會顯示目前的設定**OMP_NUM_THREADS**環境變數：  
  
```  
set OMP_NUM_THREADS  
```  
  
## <a name="see-also"></a>請參閱  
 [環境變數](../../../parallel/openmp/reference/openmp-environment-variables.md)