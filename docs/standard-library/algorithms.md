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
ms.openlocfilehash: d363dc3f06222121ac5efc79b30516ebd55ff539
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68456491"
---
# <a name="algorithms"></a>演算法

演算法是 C++ 標準程式庫的基礎部分。 演算法不會對容器本身執行，而是對迭代器執行。 因此，相同的演算法可供大部分甚至所有的 C++ 標準程式庫容器使用。 本節討論 C++ 標準程式庫演算法的慣例和術語。

## <a name="remarks"></a>備註

在說明演算法範本函式時會使用數個速記片語：

- \[「在範圍*A*, *B*中」的片語表示零個或多個離散值的順序, 開頭為最多, 但不包含*B*。只有在可從*A*連接到*B*時, 範圍才有效; 您可以將*a*儲存在物件*n* (*n*  =  *A*) 中、將物件遞增零或多次 (+ +*N*), 並讓物件比較等於*B*在有限的增量數目之後 (*N*  ==  *B*)。

- 「 \[範圍*a*, *B*中的每個*n* 」一詞表示*N*以值*a*開頭, 而且會遞增零或多次, 直到等於值*B*為止。案例 *N* == *B* 不在範圍內。

- 片語「範圍\[ *a*, *b*) 中的最小*n*值, 因此*x*」表示會為範圍\[ *a*, *b*中的每個*n*決定條件*X* , 直到符合條件*X* 。

- 片語\[「範圍*a*, *b*) 中的最大*n*值, 因此*x*表示會針對範圍 \[ *a*, *b*) 中的每個*n*決定 x。 函式會在每次符合條件*X*時, 將每個*N*的複本儲存在*K* 。 如果發生這類存放區, 函式會將*N*的最終值 (等於*B*) 取代為*K*的值。但就雙向或隨機存取迭代器而言，這也可能表示 *N* 以範圍內的最大值開頭，然後在範圍內減量直到符合條件 *X* 為止。

- *X* - *Y* 這類運算式，其中 *X* 和 *Y* 可以是隨機存取迭代器以外的迭代器，用於數學領域。 函式若必須判斷這類 **-** 值, 則不一定會評估運算子。 這同樣也適用於 *X* + *N* 和 *X* - *N*，其中 *N* 是整數類型。

有數個演算法使用述詞來執行成對比較 (例如與`operator==`), 以產生**bool**結果。 述詞函式 `operator==` (或任何替代項目) 不可變更其任一運算元。 它必須在每次評估時產生相同的**bool**結果, 而且如果任一運算元的複本都是用來替代運算元, 則必須產生相同的結果。

有數個演算法使用必須對序列中的元素配對強制執行嚴格弱式順序的述詞。 針對述詞*pred*(*X*, *Y*):

- Strict 表示*pred*(*x*, *x*) 為 false。

- 弱\!式表示如果*pred*(*X*, *y*) & \!& *pred*(*y*, *x*), *x*和*y*具有對等的順序 (*x*  ==  *y*則不會需要定義)。

- 排序表示*pred*(*x*, *Y*) & & *pred*(*Y*, *z*) 意指*pred*(*x*, z )。

其中有部分演算法會隱含地使用述詞 *X* \< *Y*。其他通常符合嚴格弱式排序需求的述詞*為 X*  >  *Y* `less`、(*X*, *y*) 和`greater`(*x*, *y*)。 但請注意，*X* \<= *Y* 和 *X* >= *Y* 之類的述詞並不符合此需求。

反覆運算器在範圍\[ *First*、 *Last*) 中所指定的專案序列, 是依運算子 **<** 排序的序列 (如果範圍 \[0 中的每個 N,*最後* - 一個是)), 並針對範圍 (*N*, \! *Last*  -  *First*) 中的每個*M* ,\*述詞 ((*前* +  *M*) < \*(前 +  *N*個)) 為 true。 (請注意，元素會以遞增順序排序)。述詞函式 `operator<` (或任何替代項目) 不可變更其任一運算元。 它必須在每次評估時產生相同的**bool**結果, 而且如果任一運算元的複本都是用來替代運算元, 則必須產生相同的結果。 此外，它必須對它所比較的運算元強制執行嚴格弱式排序。

在\[範圍 -  \[ `Last` `operator<`   內, 反覆運算器所指定的專案序列, 是依 if, 針對範圍 1, 最後一個中的每個 N 排序的堆積。 `First`\*述詞 <  _(第一個_ *(前*N 個)) 為 true。  +  \* \! (第一個元素最大。)除此之外, 只有範本函式[make_heap](../standard-library/algorithm-functions.md#make_heap)、 [pop_heap](../standard-library/algorithm-functions.md#pop_heap)和[push_heap](../standard-library/algorithm-functions.md#push_heap)才會知道其內部結構。 如同已排序的序列, `operator<`述詞函式或其任何取代項不能改變其任一運算元, 且必須對它所比較的運算元強加嚴格的弱式排序。 它必須在每次評估時產生相同的**bool**結果, 而且如果任一運算元的複本都是用來替代運算元, 則必須產生相同的結果。

C++ 標準程式庫演算法位於 [\<algorithm>](../standard-library/algorithm.md) 和 [\<numeric>](../standard-library/numeric.md) 標頭檔中。

## <a name="see-also"></a>另請參閱

[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
