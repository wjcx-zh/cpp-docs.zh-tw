---
title: "omp_set_num_threads |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: omp_set_num_threads
dev_langs: C++
helpviewer_keywords: omp_set_num_threads OpenMP function
ms.assetid: dae0bf3f-cd7a-4413-89de-6149ac1f4fa7
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 66fc3984342b75b2fed35ed9a5c58d0848d41b2c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="ompsetnumthreads"></a>omp_set_num_threads
在後續的平行區域，設定執行緒的數目，除非被[num_threads](../../../parallel/openmp/reference/num-threads.md)子句。  
  
## <a name="syntax"></a>語法  
  
```  
void omp_set_num_threads(  
   int num_threads  
);  
```  
  
## <a name="remarks"></a>備註  
 其中：  
  
 `num_threads`  
 在平行區域中的執行緒數目。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊，請參閱[3.1.1 omp_set_num_threads 函式](../../../parallel/openmp/3-1-1-omp-set-num-threads-function.md)。  
  
## <a name="example"></a>範例  
 請參閱[omp_get_num_threads](../../../parallel/openmp/reference/omp-get-num-threads.md)的使用範例`omp_set_num_threads`。  
  
## <a name="see-also"></a>另請參閱  
 [函式](../../../parallel/openmp/reference/openmp-functions.md)