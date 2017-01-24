---
title: "A.6   Using the lastprivate Clause | Microsoft Docs"
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
ms.assetid: cf3bf0cc-aa46-4e44-9433-e2969e3be2c1
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.6   Using the lastprivate Clause
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

有時候正確執行迴圈 \(loop\) 的最後一個反覆項目會指派給變數的值而定。  這種程式必須列出當做引數的所有這類變數`lastprivate`子句 \([區段 2.7.2.3](../../parallel/openmp/2-7-2-3-lastprivate.md) 在 27\] 頁面上\)，以使變數的值相同時迴圈循序執行。  
  
```  
#pragma omp parallel  
{  
   #pragma omp for lastprivate(i)  
      for (i=0; i<n-1; i++)  
         a[i] = b[i] + b[i+1];  
}  
a[i]=b[i];  
```  
  
 在上述範例中，值`i`在平行區域結尾處會等於`n–1`、 在循序的狀況下中。