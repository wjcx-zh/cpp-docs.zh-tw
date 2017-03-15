---
title: "A.27   Use of C99 Variable Length Arrays | Microsoft Docs"
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
ms.assetid: 8e542701-39f9-4f28-ab3a-840e8e669723
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.27   Use of C99 Variable Length Arrays
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例會示範如何使用可變動長度陣列 C99 \(VLAs\) 在`firstprivate`指示詞 \([區段 2.7.2.2](../../parallel/openmp/2-7-2-2-firstprivate.md) 在頁面上 26\)。  
  
> [!NOTE]
>  Visual C\+\+ 不目前支援可變長度陣列。  
  
```  
void f(int m, int C[m][m])  
{  
    double v1[m];  
    ...  
    #pragma omp parallel firstprivate(C, v1)  
    ...  
}  
```