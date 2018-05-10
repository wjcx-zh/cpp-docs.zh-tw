---
title: A.20 barrier 指示詞的繫結 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: a3fdcc26-6873-429b-998e-de451401483b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b1123ab0b4d406a613176dfcd50f459d089e45d9
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
---
# <a name="a20---binding-of-barrier-directives"></a>A.20 繫結 barrier 指示詞
指示詞的繫結規則呼叫**屏障**指示詞繫結至最接近的封閉式`parallel`指示詞。 如需詳細指示詞繫結的詳細資訊，請參閱[區段 2.8](../../parallel/openmp/2-8-directive-binding.md) 32 頁面上。  
  
 在下列範例中，從呼叫*主要*至*sub2*相容因為**屏障**(在*sub3*) 繫結至平行區域在*sub2*。 從呼叫*主要*至*sub1*相容因為**屏障**繫結至在副程式中的平行區域*sub2*。  從呼叫*主要*至*sub3*相容因為**屏障**不會連結到任何平行區域並將遭到忽略。 也請注意，**屏障**只會同步處理的封入平行區域中的執行緒並不是所有的執行緒中建立小組*sub1*。  
  
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