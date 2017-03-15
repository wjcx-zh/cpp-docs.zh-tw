---
title: "OpenMP Clauses | Microsoft Docs"
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
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# OpenMP Clauses
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

提供連結 OpenMP API 中所使用的子句。  
  
 Visual C\+\+ 中支援下列 OpenMP 子句：  
  
|子句|描述|  
|--------|--------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|允許執行緒來存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|指定一或多個變數應該分擔所有執行緒。|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|指定在平行區域中的 unscoped 變數的行為。|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|因為它存在於平行建構之前，請指定每個執行緒都應該有自己的執行個體的變數，並與變數的值，應該先初始化變數。|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|指定在平行或序列時，是否執行迴圈。|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|指定變數的封入內容的版本是等於最終的反覆項目 \(for 迴圈建構\) 或最後一個區段 \(\# pragma 區段\)，那麼無論哪一個執行緒會執行的私用版本。|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|會覆寫障盾隱含指示詞。|  
|[num\_threads](../../../parallel/openmp/reference/num-threads.md)|設定執行緒小組中的執行緒數目。|  
|[ordered](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|對於平行[for](../../../parallel/openmp/reference/for-openmp.md)陳述式如果[ordered](../../../parallel/openmp/reference/ordered-openmp-directives.md)指示詞會在迴圈中使用。|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|指定每個執行緒都應該有自己的執行個體的變數。|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|指定給每個執行緒的私用的一或多個變數都是在平行區域結尾處的縮減作業的主體。|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|適用於[for](../../../parallel/openmp/reference/for-openmp.md)指示詞。|  
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|指定一或多個變數應該分擔所有執行緒。|  
  
## 請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [Directives](../../../parallel/openmp/reference/openmp-directives.md)