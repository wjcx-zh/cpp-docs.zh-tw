---
title: 4.4 OMP_NESTED |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1779b75774a2177a0d6a4f0661406e28b479a7ee
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33690266"
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED`環境變數啟用或停用巢狀平行處理原則，除非啟用或停用藉由呼叫巢狀平行處理原則`o` **mp_set_nested**程式庫常式。 如果設定為**TRUE**，啟用巢狀平行處理原則; 如果設定為**FALSE**、 巢狀平行處理原則已停用。 預設值是**FALSE**。  
  
 範例：  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>交叉參考：  
  
-   `omp_set_nested` 函式，請參閱[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。