---
title: "屏障 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: barrier
dev_langs: C++
helpviewer_keywords: barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5d1e8076ecef41cf60bf34a0622ee53afb05910b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="barrier"></a>barrier
會同步處理所有執行緒在一個小組。在屏障的所有執行緒都暫停，直到所有執行緒都執行屏障。  
  
## <a name="syntax"></a>語法  
  
```  
#pragma omp barrier  
```  
  
## <a name="remarks"></a>備註  
 `barrier`指示詞可支援不含 OpenMP 子句。  
  
 如需詳細資訊，請參閱[2.6.3 barrier 指示詞](../../../parallel/openmp/2-6-3-barrier-directive.md)。  
  
## <a name="example"></a>範例  
 如需使用方式的範例`barrier`，請參閱[主要](../../../parallel/openmp/reference/master.md)。  
  
## <a name="see-also"></a>請參閱  
 [指示詞](../../../parallel/openmp/reference/openmp-directives.md)