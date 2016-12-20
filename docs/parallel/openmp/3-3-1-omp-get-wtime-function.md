---
title: "3.3.1 omp_get_wtime Function | Microsoft Docs"
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
ms.assetid: 90188bd2-c53e-4398-8946-d3ecc92fa0f6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 3.3.1 omp_get_wtime Function
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`omp_get_wtime`函式會傳回雙精度浮點數值等於 24 小時制的牆上的時鐘時間以秒為單位，因為某些 」 時間在過去 」。  實際"時間過去"是任意的但可保證不變更應用程式執行期間。  格式如下：  
  
```  
#include <omp.h>  
double omp_get_wtime(void);  
```  
  
 它被預期的函式將用於測量已耗用時間，如下列範例所示：  
  
```  
double start;  
double end;  
start = omp_get_wtime();  
... work to be timed ...  
end = omp_get_wtime();  
printf_s("Work took %f sec. time.\n", end-start);  
```  
  
 傳回的時間都 「 每一執行緒時段"這是不需要是全域一致參與應用程式的所有執行緒。