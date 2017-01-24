---
title: "3.1.10 omp_get_nested Function | Microsoft Docs"
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
ms.assetid: 48736a25-5c6e-4e2d-aad0-421087663a3c
caps.latest.revision: 6
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.1.10 omp_get_nested Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_nested`函式會傳回非零的值，如果巢狀的平行處理原則已啟用，0 停用。  如需有關巢狀的平行處理原則的詳細資訊，請參閱章節 3.1.9 網頁 40。  格式如下：  
  
```  
#include <omp.h>  
int omp_get_nested(void);  
```  
  
 如果實作不實作巢狀的平行處理原則，這個函式一定會傳回 0。