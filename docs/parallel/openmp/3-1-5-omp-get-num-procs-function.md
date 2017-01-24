---
title: "3.1.5 omp_get_num_procs Function | Microsoft Docs"
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
ms.assetid: bbfbf17b-0c68-4ba6-a25d-07c36ecb551f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.5 omp_get_num_procs Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_num_procs`函式會傳回所提供的程式在呼叫函式的處理器數目。  格式如下：  
  
```  
#include <omp.h>  
int omp_get_num_procs(void);  
```