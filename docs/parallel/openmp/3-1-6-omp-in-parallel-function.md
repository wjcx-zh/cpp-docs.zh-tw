---
title: "3.1.6 omp_in_parallel Function | Microsoft Docs"
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
ms.assetid: db6e3a63-2a0a-4b8e-8cc6-c6b49edca5fb
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.6 omp_in_parallel Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

**Omp\_in\_parallel** 函式會傳回非零值，如果呼叫平行; 平行區域執行的動態範圍內 否則，它會傳回 0。  格式如下：  
  
```  
#include <omp.h>  
int omp_in_parallel(void);  
```  
  
 這個函式會傳回非零的值呼叫區域執行，以平行方式，包括巢狀的區域進行序列化時。