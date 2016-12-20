---
title: "A.29   Use of Work-Sharing Constructs Inside a critical Construct | Microsoft Docs"
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
ms.assetid: d5c8a83f-2f51-4f23-8ddf-d267e347507f
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.29   Use of Work-Sharing Constructs Inside a critical Construct
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例將示範如何使用工作共用的建構內`critical`建構。  本範例是相容的因為工作共用建構和`critical`建構不要繫結至同一個平行區域。  
  
```  
void f()  
{  
  int i = 1;  
  #pragma omp parallel sections  
  {  
    #pragma omp section  
    {  
      #pragma omp critical (name)  
      {  
        #pragma omp parallel  
        {  
          #pragma omp single  
          {  
            i++;  
          }  
        }  
      }  
    }  
  }  
}  
```