---
title: 2.7.1 threadprivate 指示詞 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-parallel
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: 08e0b70f-5359-4607-b0ca-38c2d570d7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 31c9c70940b558d0b4cc3f77677665235417694d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/19/2018
ms.locfileid: "46398140"
---
# <a name="271-threadprivate-directive"></a>2.7.1 threadprivate 指示詞

`threadprivate`指示詞讓具名的檔案範圍、 命名空間範圍或靜態的區塊範圍變數中指定*變數清單*執行緒私用。 *變數清單*是沒有不完整類型的變數的逗號分隔清單。 語法`threadprivate`指示詞時，如下所示：

```
#pragma omp threadprivate(variable-list) new-line
```

每一份`threadprivate`變數會初始化一次，在未指定的時間點之前的第一個參考到該複本，計畫和一般方式 （亦即，當主要複本會初始化序列執行的程式中）。 請注意，如果在明確的初始設定式中參考物件的`threadprivate`變數和物件的值一份變數的第一個參考之前遭到修改，則行為是未指定。

如有任何私用變數，執行緒絕不能參考另一個執行緒的副本`threadprivate`物件。 在序列地區和程式的主要區域中，參考是物件的主要執行緒的複本。

執行第一個平行區域中的資料之後`threadprivate`物件一定會保存只当動態執行緒機制已停用，而如果執行緒數目維持不變，所有的平行區域。

若要限制`threadprivate`指示詞如下所示：

- A`threadprivate`檔案範圍或命名空間範圍變數的指示詞必須出現任何定義或宣告中，外部，而且必須語彙前面清單中的任何變數的所有參考。

- 在每個變數*變數清單*的`threadprivate`在語彙上位於指示詞的檔案或命名空間範圍的變數宣告必須參考指示詞檔案或命名空間的範圍。

- A`threadprivate`靜態的區塊範圍變數的指示詞必須出現在變數的範圍內，而不是在巢狀範圍。 指示詞語彙必須在所有參考任何變數都之前在其清單中。

- 在每個變數*變數清單*的`threadprivate`區塊範圍中的指示詞必須參考相同語彙前面的指示詞的範圍中的變數宣告。 變數宣告都必須使用靜態儲存類別規範。

- 如果變數中指定`threadprivate`指示詞在一個轉譯單位中，您必須指定在`threadprivate`宣告它的每一個轉譯單位的指示詞。

- A`threadprivate`變數不得出現在以外的任何子句`copyin`， `copyprivate`， `schedule`， `num_threads`，或有**如果**子句。

- 位址`threadprivate`變數不是位址是否固定。

- A`threadprivate`變數不能是不完整的類型或參考型別。

- A`threadprivate`非 POD 類別類型的變數必須可存取且明確的複製建構函式，如果它使用明確的初始設定式宣告。

下列範例說明如何修改初始設定式中出現的變數可能會導致未指定的行為，以及如何使用輔助物件和複製建構函式，以避免這個問題。

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

- 動態的執行緒，請參閱[一節 3.1.7](../../parallel/openmp/3-1-7-omp-set-dynamic-function.md) 39 頁面上。

- `OMP_DYNAMIC` 環境變數，請參閱[4.3 節](../../parallel/openmp/4-3-omp-dynamic.md)49 頁面上。