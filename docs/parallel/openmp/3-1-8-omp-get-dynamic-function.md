---
title: "3.1.8 omp_get_dynamic Function | Microsoft Docs"
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
ms.assetid: c03e2daf-29c9-49e3-9b67-b980ad1ab195
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.8 omp_get_dynamic Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_get\_dynamic** 函式會傳回非零值，如果動態調整執行緒的啟用，否則傳回 0。  格式如下：  
  
```  
#include <omp.h>  
int omp_get_dynamic(void);  
```  
  
 如果實作不實作動態調整執行緒的數目，這個函式一定會傳回 0。  
  
## 交互參照：  
  
-   如需執行緒動態調整的說明，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。