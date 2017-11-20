---
title: "4.4 OMP_NESTED |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: fd17b6f4-84e8-44c0-a96a-3a9e5ba33688
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fbb45bb04db612451c7d081f3a7afad8031da643
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="44-ompnested"></a>4.4 OMP_NESTED
`OMP_NESTED`環境變數啟用或停用巢狀平行處理原則，除非啟用或停用藉由呼叫巢狀平行處理原則`o` **mp_set_nested**程式庫常式。 如果設定為**TRUE**，啟用巢狀平行處理原則; 如果設定為**FALSE**、 巢狀平行處理原則已停用。 預設值是**FALSE**。  
  
 範例：  
  
```  
setenv OMP_NESTED TRUE  
```  
  
## <a name="cross-reference"></a>交叉參考：  
  
-   `omp_set_nested`函式，請參閱[區段 3.1.9](../../parallel/openmp/3-1-9-omp-set-nested-function.md)在 40 頁面上。