---
title: "OpenMP Directives | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
ms.assetid: 0562c263-344c-466d-843e-de830d918940
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# OpenMP Directives
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供指示詞中 OpenMP API 所使用的連結。  
  
 Visual C\+\+ 中支援下列 OpenMP 指示詞：  
  
|指示詞|描述|  
|---------|--------|  
|[atomic](../../../parallel/openmp/reference/atomic.md)|表示將會以原子方式更新的記憶體位置。|  
|[barrier](../../../parallel/openmp/reference/barrier.md)|同步處理所有的執行緒在小組 ； 在障盾的所有執行緒都暫停，直到所有的執行緒執行的屏障。|  
|[critical](../../../parallel/openmp/reference/critical.md)|指定程式碼就只能執行一個執行緒上一次。|  
|[flush](../../../parallel/openmp/reference/flush-openmp.md)|指定所有執行緒都有相同的檢視，供所有的共用物件的記憶體。|  
|[for](../../../parallel/openmp/reference/for-openmp.md)|使完成的工作執行緒之間分割為在平行區域內的迴圈。|  
|[master](../../../parallel/openmp/reference/master.md)|指定只有主版的 threadshould 執行程式的一個區段。|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md)|指定在平行化程式碼，如應該像循序迴圈中執行迴圈。|  
|[parallel](../../../parallel/openmp/reference/parallel.md)|定義在平行區域，也就是將由多個執行緒同時執行的程式碼。|  
|[sections](../../../parallel/openmp/reference/sections-openmp.md)|識別分割為所有的執行緒之間的程式碼區段。|  
|[single](../../../parallel/openmp/reference/single.md)|讓您指定一段程式碼應該會在單一執行緒，不一定是主執行緒上執行。|  
|[threadprivate](../../../parallel/openmp/reference/threadprivate.md)|指定變數是專屬於一個執行緒。|  
  
## 請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Clauses](../../../parallel/openmp/reference/openmp-clauses.md)