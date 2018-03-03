---
title: "2.7.1 threadprivate 指示詞 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 22bb7f477be397f01ee4bd82f472ff26a26ce811
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指示詞
`threadprivate`指示詞讓具名的檔案範圍、 命名空間範圍或靜態的區塊範圍變數中指定*變數清單*執行緒私用。 *變數清單*是沒有不完整類型的變數的逗號分隔清單。 語法`threadprivate`指示詞時，如下所示：  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 每個複本`threadprivate`變數會初始化一次，在未指定的時間點在程式之前的第一個參考到該複本，並以一般方式 （也就是為主要複本會初始化序列執行的程式中）。 請注意，如果在明確的初始設定式中參考物件的`threadprivate`副本變數的第一個參考之前修改變數和物件的值，則行為是未指定。  
  
 為與任何私用變數中，執行緒絕不能參考另一個執行緒副本`threadprivate`物件。 在循序區域和程式的主要區域，請參考會為物件的主執行緒的複本。  
  
 執行第一個平行區域中的資料後`threadprivate`保證只有如果動態執行緒機制已停用，而且如果執行緒數目維持不變，所有的平行區域的保存物件。  
  
 若要限制`threadprivate`指示詞如下：  
  
-   A`threadprivate`檔案範圍或命名空間範圍變數的指示詞必須出現以外任何定義或宣告中，並在語彙上皆必須在其清單中前面任何變數的所有參考。  
  
-   在每個變數*變數清單*的`threadprivate`在語彙上皆位於指示詞的檔案或命名空間範圍變數宣告必須參考指示詞在檔案或命名空間範圍。  
  
-   A`threadprivate`靜態的區塊範圍變數的指示詞必須顯示變數的範圍內，而不是在巢狀範圍。 指示詞語彙上皆必須在所有參照任何變數都之前在其清單中。  
  
-   在每個變數*變數清單*的`threadprivate`區塊範圍中的指示詞必須參考語彙之前指示詞和相同範圍中的變數宣告。 變數宣告都必須使用靜態儲存類別規範。  
  
-   如果變數中指定了`threadprivate`指示詞在一個轉譯單位中，您必須在指定`threadprivate`宣告它的每一個轉譯單位的指示詞。  
  
-   A`threadprivate`變數不能出現在以外的任何子句`copyin`， `copyprivate`， `schedule`， `num_threads`，或**如果**子句。  
  
-   位址`threadprivate`變數不是位址常數。  
  
-   A`threadprivate`變數必須沒有不完整的類型或參考類型。  
  
-   A`threadprivate`與非 POD 類別類型的變數必須可存取且明確的複製建構函式，如果它以明確的初始設定式宣告。  
  
 下列範例說明如何修改初始設定式中出現的變數可能會導致未指定的行為，以及如何使用輔助物件和複製建構函式來避免這個問題。  
  
```  
int x = 1;  
T a(x);  
const T b_aux(x); /* Capture value of x = 1 */  
T b(b_aux);  
#pragma omp threadprivate(a, b)  
  
void f(int n) {  
   x++;  
   #pragma omp parallel for  
   /* In each thread:  
   * Object a is constructed from x (with value 1 or 2?)  
   * Object b is copy-constructed from b_aux  
   */  
   for (int i=0; i<n; i++) {  
      g(a, b); /* Value of a is unspecified. */  
   }  
}  
```  
  
## <a name="cross-references"></a>交叉參考：  
  
-   動態執行緒，請參閱[區段 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。  
  
-   `OMP_DYNAMIC`環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。