---
title: barrier | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- barrier
dev_langs:
- C++
helpviewer_keywords:
- barrier OpenMP directive
ms.assetid: 5c73ad4f-c768-443a-8f9e-4fd8bc2253c7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0008c343130bf47170957204793cf3c85b22f1e3
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/23/2018
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