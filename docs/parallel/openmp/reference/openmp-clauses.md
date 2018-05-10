---
title: OpenMP 子句 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: reference
dev_langs:
- C++
ms.assetid: 806e7d8f-b204-4e4c-a12c-273ab540a7ca
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7abe5a637a2a32c696f19f5ab9988f1be361f647
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="openmp-clauses"></a>OpenMP 子句
提供子句在 OpenMP API 中使用的連結。  
  
 Visual c + + 支援下列 OpenMP 子句：  
  
|子句|描述|  
|------------|-----------------|  
|[copyin](../../../parallel/openmp/reference/copyin.md)|可讓執行緒存取主執行緒的值，如[threadprivate](../../../parallel/openmp/reference/threadprivate.md)變數。|  
|[copyprivate](../../../parallel/openmp/reference/copyprivate.md)|指定一個或多個變數，應該所有執行緒之間共用。|  
|[default](../../../parallel/openmp/reference/default-openmp.md)|指定在平行區域不限範圍變數的行為。|  
|[firstprivate](../../../parallel/openmp/reference/firstprivate.md)|指定每個執行緒都應該有自己的變數中，執行個體和具有變數的值，應該先初始化變數，因為它存在於平行建構之前。|  
|[if](../../../parallel/openmp/reference/if-openmp.md)|指定在平行或序列中，是否應該執行迴圈。|  
|[lastprivate](../../../parallel/openmp/reference/lastprivate.md)|指定變數的版本，封入內容設定等於私用版本的任何執行緒執行的最後一個反覆項目 （如迴圈建構） 或最後一節 （#pragma 區段）。|  
|[nowait](../../../parallel/openmp/reference/nowait.md)|指示詞中隱含屏障會覆寫。|  
|[num_threads](../../../parallel/openmp/reference/num-threads.md)|在執行緒小組設定執行緒的數目。|  
|[排序](../../../parallel/openmp/reference/ordered-openmp-clauses.md)|平行上需要[如](../../../parallel/openmp/reference/for-openmp.md)陳述式如果[排序](../../../parallel/openmp/reference/ordered-openmp-directives.md)指示詞是用在迴圈中。|  
|[private](../../../parallel/openmp/reference/private-openmp.md)|指定每個執行緒都應該有自己的執行個體的變數。|  
|[reduction](../../../parallel/openmp/reference/reduction.md)|指定每個執行緒私用的一個或多個變數是減少作業在平行區域結尾處的主題。|  
|[schedule](../../../parallel/openmp/reference/schedule.md)|適用於[如](../../../parallel/openmp/reference/for-openmp.md)指示詞。|  
|[shared](../../../parallel/openmp/reference/shared-openmp.md)|指定一個或多個變數，應該所有執行緒之間共用。|  
  
## <a name="see-also"></a>另請參閱  
 [OpenMP](../../../parallel/openmp/openmp-in-visual-cpp.md)   
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)