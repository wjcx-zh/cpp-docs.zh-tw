---
title: "A.19 範例會顯示不正確的巢狀工作共用指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 906e900d-9259-44d6-a095-c1ba9135d269
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1cc5ed3a3a5ddd4117a3332703613a8d525853a8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="a19---examples-showing-incorrect-nesting-of-work-sharing-directives"></a>A.19 巢狀使用工作共用指示詞的錯誤範例
本節中的範例說明的指示詞的巢狀規則。 如需詳細指示詞的巢狀結構的詳細資訊，請參閱[區段 2.9](../../parallel/openmp/2-9-directive-nesting.md) 33 頁面上。  
  
 下列範例是不符合規定因為內部和外部`for`指示詞為巢狀，並繫結至相同`parallel`指示詞：  
  
```  
void wrong1(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
      int i, j;  
      #pragma omp for  
      for (i=0; i<n; i++) {  
          #pragma omp for  
              for (j=0; j<n; j++)  
                 work(i, j);  
     }  
   }  
}  
```  
  
 前述範例中的下列動態巢狀的版本也是不相容：  
  
```  
void wrong2(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++)  
        work1(i, n);  
  }  
}  
  
void work1(int i, int n)  
{  
  int j;  
  #pragma omp for  
    for (j=0; j<n; j++)  
      work2(i, j);  
}  
```  
  
 下列範例是不符合規定因為`for`和`single`指示詞為巢狀，並繫結到相同的平行區域：  
  
```  
void wrong3(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        #pragma omp single  
          work(i);  
      }  
  }  
}  
```  
  
 下列範例是不符合規定因為`barrier`指示詞內`for`可能會導致死結：  
  
```  
void wrong4(int n)  
{  
  #pragma omp parallel default(shared)  
  {  
    int i;  
    #pragma omp for  
      for (i=0; i<n; i++) {  
        work1(i);  
        #pragma omp barrier  
        work2(i);  
      }  
  }  
}  
```  
  
 下列範例是不符合規定因為`barrier`導致死結，因為用一次只有一個執行緒可以進入關鍵區段：  
  
```  
void wrong5()  
{  
  #pragma omp parallel  
  {  
    #pragma omp critical  
    {  
       work1();  
       #pragma omp barrier  
       work2();  
    }  
  }  
}  
```  
  
 下列範例是不符合規定因為`barrier`導致死結，因為，只有一個執行緒執行`single`> 一節：  
  
```  
void wrong6()  
{  
  #pragma omp parallel  
  {  
    setup();  
    #pragma omp single  
    {  
      work1();  
      #pragma omp barrier  
      work2();  
    }  
    finish();  
  }  
}  
```