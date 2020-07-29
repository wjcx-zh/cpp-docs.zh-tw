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
ms.openlocfilehash: 6532cb56bb70c82525a13ba53efdd6203ebafb12
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87205219"
---
# <a name="algorithms"></a>演算法

演算法是 C++ 標準程式庫的基礎部分。 演算法不會對容器本身執行，而是對迭代器執行。 因此，相同的演算法可供大部分甚至所有的 C++ 標準程式庫容器使用。 本節討論 C++ 標準程式庫演算法的慣例和術語。

## <a name="remarks"></a>備註

在說明演算法範本函式時會使用數個速記片語：

- 「在範圍 \[ *A*， *B*中」的片語表示零個或多個離散值的順序，開頭*為*最多，但不包含*B*。只有在可從*A*連接到*b*時，範圍才有效; 您可以將*a*儲存在物件*n* （*n*  =  *A*）中、將物件遞增零或多次（+ +*N*），並在有限的遞增數（*N*B）之後讓物件比較等於*B*  ==  * *。

- 「範圍 a，B 中的每個*n* 」一詞 \[ *A*表示*N*以值*a*開頭，而且會遞增零或多次，直到等於值*B*為止。 *B*案例*N*  ==  *B*不在範圍內。

- 片語「範圍 a，b）中的最小*n*值 \[ * *，因此*x*」表示會針對範圍*B*a，b）中的每個*n*決定條件*x* \[ ， *B*直到符合條件*x*為止。 *A*

- 片語「範圍 a，b）中的最大*n*值 \[ *A* * *，因此*x*表示會針對範圍*X* *N* \[ *a*， *b*）中的每個 n 決定 x。 函式會在每次符合條件*X*時，將每個*N*的複本儲存在*K* 。 如果發生這類存放區，函式會將*N*的最終值（等於*B*）取代為*K*的值。不過，如果是雙向或隨機存取反覆運算器，它也可能表示*N*以範圍中的最大值為開頭，而且會在範圍中遞減，直到符合條件*X*為止。

- *X*  -  *Y*等運算式（其中*x*和*Y*可以是隨機存取反覆運算器以外的反覆運算器）是以數學意義為目標。 函式 **-** 若必須判斷這類值，則不一定會評估運算子。 這同樣也適用于*x*  +  *n*和*x*  -  *n*等運算式，其中*N*是整數類型。

有數個演算法使用述詞來執行成對比較（例如與 `operator==` ），以產生 **`bool`** 結果。 述詞函式 `operator==` (或任何替代項目) 不可變更其任一運算元。 它必須在 **`bool`** 每次評估時產生相同的結果，而且如果任一運算元的複本都是用來替代運算元，則必須產生相同的結果。

有數個演算法使用必須對序列中的元素配對強制執行嚴格弱式順序的述詞。 針對述詞*pred*（*X*， *Y*）：

- Strict 表示*pred*（*x*， *x*）為 false。

- 弱式表示*X*如果*Y* \! *pred*（*x*， *y*）  && \! *pred*（*Y*， *x*）（* *  ==  不需要定義 x*Y* ），x 和 y 具有對等的順序。

- 排序表示*pred*（*x*， *Y*）  && *pred*（*Y*， *z*）意指*pred*（*x*， *z*）。

其中一些演算法會隱含地使用述詞*X* \< *Y*. Other predicates that typically satisfy the strict weak ordering requirement are *X* > *Y*、 `less` （*x*， *y*）和 `greater` （*x*， *y*）。 不過要注意的是， *X* Y 之類的述詞 \<= *Y* and *X* > =  *Y*並不符合這項需求。

反覆運算器在範圍 First、last）中所指定的一系列專案， \[ *First*是依運算子排序的*Last*序列（ **<** 若為0、最後一個範圍中的每個*n* ）， \[ *Last*  -  *First*以及範圍內的每個*M* （*n*，*最後*  -  *一個*）述詞 \! （ \* （*第一個*  +  *M*） < \* （*前*  +  *n*個））為 true。 （請注意，元素會以遞增順序排序）。述詞函式 `operator<` （或任何取代）不得改變其任一運算元。 它必須在 **`bool`** 每次評估時產生相同的結果，而且如果任一運算元的複本都是用來替代運算元，則必須產生相同的結果。 此外，它必須對它所比較的運算元強制執行嚴格弱式排序。

在範圍內，反覆運算器所指定的專案序列 \[ `First` ， `Last` 是依 `operator<` if，針對範圍*N* \[ 1，*最後*  -  *一個第一個*中的每個 N）述詞 \! （ \* _第_一個  <  \* （*前*  +  *N*個））為 true 排序的堆積。 （第一個元素是最大值）。除此之外，只有範本函式[make_heap](algorithm-functions.md#make_heap)、 [pop_heap](algorithm-functions.md#pop_heap)和[push_heap](algorithm-functions.md#push_heap)才知道它的內部結構。 如同已排序的序列，述詞函式 `operator<` 或其任何取代項不能改變其任一運算元，且必須對它所比較的運算元強加嚴格的弱式排序。 它必須在 **`bool`** 每次評估時產生相同的結果，而且如果任一運算元的複本都是用來替代運算元，則必須產生相同的結果。

C + + 標準程式庫演算法位於 [\<algorithm>](algorithm.md) 和 [\<numeric>](numeric.md) 標頭檔中。

## <a name="see-also"></a>另請參閱

[C + + 標準程式庫參考](cpp-standard-library-reference.md)\
[C + + 標準程式庫中的執行緒安全](thread-safety-in-the-cpp-standard-library.md)
