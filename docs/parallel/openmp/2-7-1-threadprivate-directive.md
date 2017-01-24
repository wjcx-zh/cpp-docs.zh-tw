---
title: "2.7.1 threadprivate Directive | Microsoft Docs"
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
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# 2.7.1 threadprivate Directive
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

`threadprivate`指示詞會使已命名的檔案範圍、 命名空間範圍\] 或控制台中的靜態的區塊範圍變數*變數清單*專屬於一個執行緒。  *變數清單*是逗點分隔的清單不會有不完整型別變數。  語法`threadprivate`指示詞時，如下所示：  
  
```  
#pragma omp threadprivate(variable-list) new-line  
```  
  
 每一份`threadprivate`變數已初始化一次，在未指定的點，在第一次參考到該複本中，於程式中，並以平常的方式 \(也就是像主複本會初始化序列執行的程式中\)。  請注意，如果在明確的初始設定式中參考物件時`threadprivate`變數和物件的值修改之前為該變數，一份的第一個參考，那麼行為是未指定。  
  
 如有任何私用變數，執行緒不得參考另一個執行緒的複本`threadprivate`物件。  在序列的區域與程式的主要區域，參考將會以物件的主執行緒的複本。  
  
 執行第一個平行區域中的資料之後`threadprivate`保證物件會保存純如果動態執行緒機制已停用時，執行緒的數目會維持不變的所有平行區域。  
  
 若要限制`threadprivate`指示詞如下：  
  
-   A `threadprivate`檔案範圍或命名空間範圍變數的指示詞必須出現外的任何定義或宣告，而且必須在語彙上之前所有的參考至任一個變數在其清單中。  
  
-   在每個變數*變數清單*的`threadprivate`指示詞在檔案或命名空間的範圍，必須指向在語彙上之前的指示詞的檔案或命名空間範圍變數宣告。  
  
-   A `threadprivate`的靜態的區塊範圍變數的指示詞必須出現在變數的範圍，而不是在巢狀的範圍內。  指示詞必須在前面語彙上任何變數的所有參考清單中。  
  
-   在每個變數*變數清單*的`threadprivate`區塊範圍內的指示詞必須是指向變數的宣告語彙上之前的指示詞與相同範圍中。  變數的宣告必須使用靜態儲存類別規範。  
  
-   如果變數在指定`threadprivate`指示詞在一個轉譯單位中，必須指定它在`threadprivate`指示詞宣告它的每一個轉譯單位中。  
  
-   A `threadprivate`變數必須出現在任何子句除了`copyin`， `copyprivate`， `schedule`， `num_threads`，或**如果**子句。  
  
-   位址`threadprivate`變數不是地址常數。  
  
-   A `threadprivate`變數不能不完整型別或參考型別。  
  
-   A `threadprivate`變數與非 POD 類別型別必須可存取的、 模稜兩可的複製建構函式，如果它以明確的初始設定式宣告。  
  
 下列範例說明如何修改此變數會出現在 \[初始設定式可能會造成未指定的行為，以及如何使用輔助的物件，並複製建構函式來避免這個問題。  
  
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
  
## 交互參照：  
  
-   動態的執行緒，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 在 39\] 頁面上。  
  
-   `OMP_DYNAMIC`環境變數，請參閱 [4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)在 49\] 頁面上。