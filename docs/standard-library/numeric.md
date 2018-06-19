---
title: '&lt;numeric&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <numeric>
dev_langs:
- C++
helpviewer_keywords:
- <numeric> header
ms.assetid: 6d6ccb94-48cc-479b-b4a9-bd9c78d4896a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c5705414bdc6915e758d66576855a45db5fcad23
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
ms.locfileid: "33853111"
---
# <a name="ltnumericgt"></a>&lt;numeric&gt;

定義可執行數值處理演算法的容器樣板函式。

## <a name="syntax"></a>語法

```cpp
#include <numeric>
```

## <a name="remarks"></a>備註

數值演算法與「C++ 標準程式庫」演算法的 [\<algorithm>](algorithm.md) 類似，可在各種資料結構上操作。 這些包括標準程式庫容器類別，例如 [vector](../standard-library/vector-class.md) 和 [list](../standard-library/list-class.md)，以及滿足特定演算法需求的程式定義資料結構和元素陣列。 演算法間接透過迭代器存取和周遊容器的項目，來達成這個一般性層級。 演算法處理迭代器範圍 (通常由其開始或結束位置指定)。 參考的範圍必須是有效的，這表示在範圍內的所有指標必須都是可取值且在每個範圍的序列中，而且最後一個位置必須可透過遞增從第一個位置連接。

演算法可延伸每一個「C++ 標準程式庫」容器的作業和成員函式所支援的動作，而且能夠同時與不同類型的容器物件互動。

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[accumulate](../standard-library/numeric-functions.md#accumulate)|透過計算後續部分總和，計算在指定範圍中所有項目的總和 (包括特定初始值)，或計算後續部分結果 (取得方式是使用指定的二進位運算而非總和運算) 的結果。|
|[adjacent_difference](../standard-library/numeric-functions.md#adjacent_difference)|計算在輸入範圍中每個項目及其前置項之間的後續差異並將結果輸出至目的範圍，或計算一般化程序的結果，其中由另一個指定的二進位運算取代差異作業。|
|[inner_product](../standard-library/numeric-functions.md#inner_product)|計算兩個範圍的項目乘積的總和並將它加入至指定的初始值，或計算一般化程序的結果，其中由另一個指定的二進位運算取代總和與乘積運算。|
|[iota](../standard-library/numeric-functions.md#iota)|儲存開始值，從第一個項目開始，並在間隔 `value++` 中每一個項目，以值的後續增量 (`[first, last)`) 填滿。|
|[partial_sum](../standard-library/numeric-functions.md#partial_sum)|計算在輸入範圍中從第一個元素到第 *i* 個元素的一系列總和，然後將每個總和的結果儲存在目的範圍的第 *i* 個元素中，或計算一般化程序的結果，其中總和運算會由另一個指定的二進位運算取代。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
