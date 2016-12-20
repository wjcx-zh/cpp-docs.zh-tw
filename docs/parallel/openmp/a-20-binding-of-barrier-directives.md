---
title: "A.20   Binding of barrier Directives | Microsoft Docs"
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
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# A.20   Binding of barrier Directives
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

指示詞的繫結規則呼叫**障盾**指示詞，以繫結至最接近的封入`parallel`指示詞。  如需有關指示詞的繫結的詳細資訊，請參閱[一節 2.8](../../parallel/openmp/2-8-directive-binding.md) 在 32\] 頁面上。  
  
 在下列範例中，從呼叫*主要* 到  *sub2* 是相容，因為**障盾** \(在  *sub3*\) 繫結至在平行區域  *sub2*。  從呼叫*主要* 到  *sub1* 是相容，因為**障盾** 繫結至副程式在平行區域  *sub2*。  從呼叫*主要* 到  *sub3* 是相容，因為**障盾**不是繫結至任何平行區域，且會被忽略。  另外請注意， **障盾** 只會同步封入的平行區域中的執行緒中建立的不是所有執行緒的群  *sub1*。  
  
```  
int main()  
{  
    sub1(2);  
    sub2(2);  
    sub3(2);  
}  
  
void sub1(int n)  
{  
    int i;  
    #pragma omp parallel private(i) shared(n)  
    {  
        #pragma omp for  
        for (i=0; i<n; i++)  
            sub2(i);  
    }  
}  
  
void sub2(int k)  
{  
     #pragma omp parallel shared(k)  
     sub3(k);  
}  
  
void sub3(int n)  
{  
    work(n);  
    #pragma omp barrier  
    work(n);  
}  
```