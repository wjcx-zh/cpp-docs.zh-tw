---
title: "A.9   Using single Directives | Microsoft Docs"
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
ms.assetid: 0c0f9495-5794-4db9-883b-a12e3a9f1328
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.9   Using single Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

下列範例會示範`single`指示詞 \([一節 2.4.3](../../parallel/openmp/2-4-3-single-construct.md) 在頁面上 15\)。  在範例中，只有一個執行緒 \(通常發生在第一個執行緒`single`指示詞\) 列印進度訊息。  使用者必須不做任何假設，到哪一個執行緒會執行`single`一節。  將略過其他所有執行緒`single`區段，然後在障盾結尾處停止`single`建構。  如果其他執行緒才能繼續而不需等待執行緒執行`single` \] 區段中， `nowait`子句可以指定在`single`指示詞。  
  
```  
#pragma omp parallel  
{  
    #pragma omp single  
        printf_s("Beginning work1.\n");  
    work1();  
    #pragma omp single  
        printf_s("Finishing work1.\n");  
    #pragma omp single nowait  
        printf_s("Finished work1 and beginning work2.\n");  
    work2();  
}  
```