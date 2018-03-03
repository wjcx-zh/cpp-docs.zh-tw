---
title: "3.1.8 omp_get_dynamic 函式 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bd4ec73b82848efcdface781738639b05a256958
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="318-ompgetdynamic-function"></a>3.1.8 omp_get_dynamic 函式
**Omp_get_dynamic**函式會傳回非零值，如果執行緒的動態調整已啟用，否則傳回 0。 格式如下：  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 如果實作不會實作動態調整執行緒數目，此函式一律傳回 0。  
  
## <a name="cross-references"></a>交叉參考：  
  
-   如需動態執行緒調整的說明，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。