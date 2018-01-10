---
title: "OpenMP 指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 51d501139d0610d670f7d646dc985a694a5b741c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="openmp-directives"></a>OpenMP 指示詞
提供使用 OpenMP API 中的指示詞連結。  
  
 Visual c + + 支援下列 OpenMP 指示詞：  
  
|指示詞|描述|  
|---------------|-----------------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|指定將自動更新的記憶體位置。|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|會同步處理所有執行緒在一個小組。在屏障的所有執行緒都暫停，直到所有執行緒都執行屏障。|  
|[critical](../../../parallel/openmp/reference/critical.md)|指定一次只在一個執行緒上執行的程式碼。|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定所有執行緒都有相同檢視的所有共用物件的記憶體。|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|會導致在執行工作分割為個執行緒在平行區域內的迴圈。|  
|[master](../../../parallel/openmp/reference/master.md)|指定只有主要 threadshould 執行的程式 > 一節。|  
|[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定應該執行迴圈，像是循序迴圈平行化該程式碼。|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|定義在平行區域，也就是將由多個執行緒以平行方式執行的程式碼。|  
|[區段](../../../parallel/openmp/reference/sections-openmp.md)|識別要當做被除數所有執行緒之間的程式碼區段。|  
|[single](../../../parallel/openmp/reference/single.md)|可讓您指定一段程式碼，應該會在單一執行緒，而不一定是主要的執行緒上執行。|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定在執行緒私用變數。|  
  
## <a name="see-also"></a>請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [子句](../../../parallel/openmp/reference/openmp-clauses.md)