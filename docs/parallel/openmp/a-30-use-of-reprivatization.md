---
title: "A.30   Use of Reprivatization | Microsoft Docs"
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
ms.assetid: 26529090-6c39-40f2-b806-e12374d6b5f8
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.30   Use of Reprivatization
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例會示範變數的 reprivatization。  可以標示為私用變數`private`一次在巢狀指示詞。  它們並沒有封入的平行區域內共用。  
  
```  
int i, a;  
...  
#pragma omp parallel private(a)  
{  
  ...  
  #pragma omp parallel for private(a)  
  for (i=0; i<10; i++)  
     {  
       ...  
     }  
}  
```