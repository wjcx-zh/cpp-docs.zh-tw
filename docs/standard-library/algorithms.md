---
title: 演算法
ms.date: 10/18/2018
helpviewer_keywords:
- libraries [C++], C++ algorithm conventions
- algorithms [C++], C++
- C++ Standard Library, algorithms
- algorithm template function C++ library conventions
- conventions [C++], C++ algorithm
ms.assetid: dec9b373-7d5c-46cc-b7d2-21a938ecd0a6
ms.openlocfilehash: a0a1165d731e44568d530e3ed919d73e2a3e8e5e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648018"
---
# <a name="algorithms"></a>演算法

演算法是 C++ 標準程式庫的基礎部分。 演算法不會對容器本身執行，而是對迭代器執行。 因此，相同的演算法可供大部分甚至所有的 C++ 標準程式庫容器使用。 本節討論 C++ 標準程式庫演算法的慣例和術語。

## <a name="remarks"></a>備註

在說明演算法範本函式時會使用數個速記片語：

- 片語 「 範圍內\[ *A*， *B*) 」 表示序列的開頭的零或多個離散的值*A*但不是包括*B*.範圍是否可有效才*B*從可觸達*A;* 您可以儲存*A*物件中*N* (*N*  = *A*)，遞增物件零或多次 (+ +*N*)，並讓物件比較等於*B*增量有限次數之後 (*N*  ==  *B*)。

- 片語 「 每個*N*範圍內\[ *A*， *B*) 」 表示*N*開頭的值並增量零或多次直到等於值*B*。案例 N == B* 不在範圍內。

- 片語 「 的最小值*N*範圍內\[ *A*， *B*) 使得*X*」 表示條件*X*決定每個*N*範圍\[ *A*， *B*) 直到條件*X*成立。

- 片語 「 的最大值*N*範圍內\[ *A*， *B*) 使得*X*表示*X*決定每個*N*範圍內\[ *A*， *B*)。 函式會儲存在*K*副本*N*每次條件*X*成立。 任何這類儲存時，此函式會取代的最終值*N*，哪一個 equals *B*，其值為*K*。但就雙向或隨機存取迭代器而言，這也可能表示 *N* 以範圍內的最大值開頭，然後在範圍內減量直到符合條件 *X* 為止。

- *X* - *Y* 這類運算式，其中 *X* 和 *Y* 可以是隨機存取迭代器以外的迭代器，用於數學領域。 此函式不一定會評估 operator **-** 必須判斷這類值時。 這同樣也適用於 *X* + *N* 和 *X* - *N*，其中 *N* 是整數類型。

有數種演算法使用的述詞執行的成對比較，例如，使用`operator==`，以產生**bool**結果。 述詞函式 `operator==` (或任何替代項目) 不可變更其任一運算元。 它必須產生相同**bool**造成每次評估時，它必須產生相同的結果，如果任一個運算元的複本替代運算元。

有數個演算法使用必須對序列中的元素配對強制執行嚴格弱式順序的述詞。 述詞*pred*(*X*， *Y*):

- 嚴格表示*pred*(*X*， *X*) 為 false。

- 弱式表示*X*並*Y*有對等排序 if \! *pred*(*X*， *Y*)& & \! *pred*(*Y*， *X*) (*X* == *Y*不需要定義)。

- 排序表示*pred*(*X*， *Y*) （& s) （& s) *pred*(*Y*， *Z*)意指*pred*(*X*， *Z*)。

其中有部分演算法會隱含地使用述詞 *X* \< *Y*。其他通常符合嚴格弱式排序需求的述詞包括*X* > *Y*， `less`(*X*， *Y*)，並`greater`(*X*， *Y*)。 但請注意，*X* \<= *Y* 和 *X* >= *Y* 之類的述詞並不符合此需求。

迭代器範圍中所指定的元素序列\[*第一次*，*最後*) 是運算子所排序的序列**<** if、 為每個*N*範圍內\[0，*上次* - *第一個*) 和每個*M*範圍內 (*N*，*上次* - *第一次*) 的述詞\!(\*(*第一個* +  *M*) < \*(*第一次* + *N*)) 為 true。 (請注意，元素會以遞增順序排序)。述詞函式 `operator<` (或任何替代項目) 不可變更其任一運算元。 它必須產生相同**bool**造成每次評估時，它必須產生相同的結果，如果任一個運算元的複本替代運算元。 此外，它必須對它所比較的運算元強制執行嚴格弱式排序。

迭代器範圍中所指定的元素序列\[ `First`， `Last`) 的已排序的堆積`operator<`if、 每個*N*範圍中\[1，*上次* - *第一次*) 的述詞\!(\*_第一個_ < \*(*第一個* + *N*)) 為 true。 (第一個元素最大。)其內部結構否則只有知道範本函式[make_heap](../standard-library/algorithm-functions.md#make_heap)， [pop_heap](../standard-library/algorithm-functions.md#pop_heap)，並[push_heap](../standard-library/algorithm-functions.md#push_heap)。 與排序順序相同，述詞函式`operator<`，或任何替代項目，不可變更其任一運算元，且它必須強制執行嚴格弱式排序它所比較的運算元。 它必須產生相同**bool**造成每次評估時，它必須產生相同的結果，如果任一個運算元的複本替代運算元。

C++ 標準程式庫演算法位於 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 標頭檔中。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
