---
title: 2.7.2.6 減少 |Microsoft 文件
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 759a2ee50f047fbd5777481d009332be998ad359
ms.sourcegitcommit: 7019081488f68abdd5b2935a3b36e2a5e8c571f8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33688800"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

這個子句會出現在純量變數上執行減少*變數清單*，與運算子*op*。 語法`reduction`子句如下所示：

> 減少 (*op*:*變數清單*)

通常會減少指定陳述式具有下列格式之一：

> *x* = *x* *op* *expr*  
> *x* *binop* = *expr*  
> *x* = *expr* *op* *x* （除了減法）  
> *x*++  
> ++*x*  
> *x*--  
> --*x*  

其中：

*x*  
其中一個削減變數中指定`list`。

*variable-list*  
純量減少變數以逗號分隔清單。

*expr*  
未參考的純量型別運算式*x*。

*Op*  
無法多載的運算子，但有一個 +、 &#42;、-、 &amp;，^， &#124;， &amp; &amp;，或&#124; &#124;。

*binop*  
無法多載的運算子，但有一個 +、 &#42;、-、 &amp;，^，或&#124;。

以下是範例`reduction`子句：  
  
```cpp  
#pragma omp parallel for reduction(+: a, y) reduction(||: am)  
for (i=0; i<n; i++) {  
   a += b[i];  
   y = sum(y, c[i]);  
   am = am || b[i] == c[i];  
}  
```  
  
此範例所示，操作員可能會隱藏函式呼叫內。 使用者應該要特別小心確認運算子中指定`reduction`子句與相符的削減作業。

雖然的右運算元&#124;&#124;運算子有沒有副作用，在此範例中，它們允許的但應該小心使用。 在此內容中，保證不會循序執行迴圈期間發生的副作用可能會平行執行期間發生。 因為執行反覆項目順序皆不明確，可能會發生這項差異。

運算子用來判斷編譯器所使用，以減少任何私用變數的初始值，以及決定最終處理運算子。 明確指定運算子可讓超出建構的語彙範圍的減少陳述式。 任何數目的`reduction`子句可指定指示詞，但變數可能會出現在最多一個`reduction`該指示詞子句。

每個變數中的私用複本*變數清單*建立時，一個用於每個執行緒，如同`private`所使用的子句。 私用複本會根據運算子初始化 （請參閱下表）。

在其區域結尾`reduction`指定子句，原始物件也會更新以反映結合其原始的值與每個使用指定的運算子的私用複製的最後一個值的結果。 削減運算子 （除了減號）、 所有關聯，而且編譯器可以自由地重新關聯，以計算最終的值。 （部分減法減少的結果會加入至表單的最終值）。

當第一個執行緒到達包含子句，並保持不變，直到完成為止，以減少計算的原始物件的值會變成不定。  一般來說，計算就會完成結尾的建構。不過，如果`reduction`子句用於將建構`nowait`是另外套用原始物件的值會維持不定之前已執行屏障同步處理，以確保所有執行緒都完成`reduction`子句。

下表列出有效的運算子和其標準初始化值。 實際的初始化值會與削減變數的資料型別一致。

|運算子|初始化|
|--------------|--------------------|
|+|0|
|&#42;|1|
|-|0|
|&amp;|~0|
|&#124;|0|
|^|0|
|&amp;&amp;|1|
|&#124;&#124;|0|

若要限制`reduction`子句如下：

- 中的變數類型`reduction`子句必須適用於削減運算子，不同之處在於不允許指標類型和參考型別。

- 中指定的變數`reduction`子句不能**const**-限定。

- 變數是在平行區域內的私用或會出現在`reduction`子句**平行**指示詞中不能指定`reduction`繫結至平行建構工作共用指示詞上的子句。

   ```cpp
   #pragma omp parallel private(y)
   { /* ERROR - private variable y cannot be specified
                in a reduction clause */
      #pragma omp for reduction(+: y)
      for (i=0; i<n; i++)
         y += b[i];
   }
   
   /* ERROR - variable x cannot be specified in both
              a shared and a reduction clause */
   #pragma omp parallel for shared(x) reduction(+: x)
   ```
