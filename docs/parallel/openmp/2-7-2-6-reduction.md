---
title: 2.7.2.6 reduction
ms.date: 11/04/2016
ms.assetid: e7630a15-2978-4dbe-a29b-3a46371a0151
ms.openlocfilehash: 54b326feb4e4ccf1f1da5c8152ffc8d1e4bd13b2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50456013"
---
# <a name="2726-reduction"></a>2.7.2.6 reduction

這個子句會減少執行上會出現在純量變數*變數清單*，與運算子*op*。 語法`reduction`子句如下所示：

> 減少 (*op*:*變數清單*)

減少通常被指定的陳述式，使用下列格式之一：

> *x* = *x* *op* *expr*
> *x* *binop* =*expr*
> *x* = *expr* *op* *x* （除外用於減法） *x*++
> ++*x*
> *x*--
> --*x*

其中：

*x*<br/>
其中一個減少變數中指定`list`。

*variable-list*<br/>
純量削減變數的逗號分隔清單。

*expr*<br/>
未參考的純量類型的運算式*x*。

*op*<br/>
無法多載的運算子，但其中一個 +， &#42;、-， &amp;，^， &#124;， &amp; &amp;，或&#124; &#124;。

*binop*<br/>
無法多載的運算子，但其中一個 +， &#42;、-， &amp;，^，或&#124;。

以下是範例`reduction`子句：

```cpp
#pragma omp parallel for reduction(+: a, y) reduction(||: am)
for (i=0; i<n; i++) {
   a += b[i];
   y = sum(y, c[i]);
   am = am || b[i] == c[i];
}
```

此範例所示，操作員可能會隱藏函式呼叫。 使用者應該要小心中指定的運算子`reduction`子句與相符的削減作業。

雖然的右運算元&#124;&#124;運算子會在此範例中沒有任何副作用，它們允許，但是應該要小心使用。 在此情況下，平行執行期間可能發生保證不會循序執行迴圈期間發生的副作用。 這項差異可能是因為反覆執行的順序為不定。

運算子用來判斷編譯器所使用，以減少任何私用變數的初始值，以及決定最終處理運算子。 明確指定運算子，可讓要建構的語彙範圍外的縮減陳述式。 任意數目的`reduction`子句可指定指示詞，但變數可能會出現在最多一個`reduction`該指示詞子句。

每個變數中的私用複本*變數清單*建立時，一個用於每個執行緒，如同`private`子句已使用。 根據運算子初始化私用複本 （請參閱下表）。

為其區域結尾`reduction`指定子句，原始的物件會更新以反映合併其原始的值，與每個使用指定的運算子的私用複本的最終值的結果。 減少運算子 （除了減）、 所有關聯，而且編譯器可以自由重新關聯，以計算最終的值。 （以形成最後的值會加入減法減少部分結果）。

當第一個執行緒到達包含子句，並保持不變，減少計算完成之前，原始物件的值會變成不定。  一般來說，計算會完整建構; 結尾不過，如果`reduction`子句可在其中建構`nowait`是另外套用原始物件的值直到不定已執行的屏障同步處理，以確保所有執行緒都已都完成`reduction`子句。

下表列出有效的運算子和其標準的初始化值。 實際的初始化值會與削減變數的資料類型一致。

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

若要限制`reduction`子句如下所示：

- 中的變數類型`reduction`子句必須適用於削減運算子，不同之處在於永遠不會允許指標型別和參考型別。

- 中指定的變數`reduction`子句不能**const**-限定。

- 在平行區域內的私用，或出現在中的變數`reduction`子句**平行**指示詞中不能指定`reduction`繫結至平行建構之工作共用指示詞子句。

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
