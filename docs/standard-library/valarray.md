---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 8b8118722d7219e3b30e11ad67411595c3dc36ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365412"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

定義範本類別 valarray 和許多支援的範本類別和函式。

## <a name="syntax"></a>語法

```cpp
#include <valarray>
```

## <a name="remarks"></a>備註

這些範本類別和函式為了改善效能，可允許不尋常的範圍。 具體而言，任何函式會傳回型別`valarray<T1>`可能會傳回某些其他 T2 類型的物件。 在此情況下，任何函式會接受一或多個引數的型別`valarray<T2>`必須具有接受這些引數，每個都取代 T2 類型的引數任意組合的多載。

### <a name="functions"></a>函式

|功能|描述|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的絕對值相等。|
|[acos](../standard-library/valarray-functions.md#acos)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反餘弦值相等。|
|[asin](../standard-library/valarray-functions.md#asin)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正弦值相等。|
|[atan](../standard-library/valarray-functions.md#atan)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正切主值相等。|
|[atan2](../standard-library/valarray-functions.md#atan2)|傳回 valarray，而常數及 valarray 項目組合指定之笛卡兒座標分量的反正切值會與其中的項目相等。|
|[cos](../standard-library/valarray-functions.md#cos)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的餘弦值相等。|
|[cosh](../standard-library/valarray-functions.md#cosh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲餘弦值相等。|
|[exp](../standard-library/valarray-functions.md#exp)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然指數值相等。|
|[log](../standard-library/valarray-functions.md#log)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然對數值相等。|
|[log10](../standard-library/valarray-functions.md#log10)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的常用對數值 (底數為 10 的對數) 相等。|
|[pow](../standard-library/valarray-functions.md#pow)|在輸入的 valarray 項目和常數上運作，傳回 valarray，其中的項目等於指定基底以指定指數自乘的乘冪，而該基底由輸入的 valarray 之項目指定或由常數指定，且該指數由輸入的 valarray 或常數指定。|
|[sin](../standard-library/valarray-functions.md#sin)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正弦值相等。|
|[sinh](../standard-library/valarray-functions.md#sinh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正弦值相等。|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的平方根相等。|
|[swap](../standard-library/valarray-functions.md#swap)||
|[tan](../standard-library/valarray-functions.md#tan)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正切值相等。|
|[tanh](../standard-library/valarray-functions.md#tanh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正切值相等。|

### <a name="operators"></a>運算子

|運算子|描述|
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|測試兩個大小相等之 valarray 的對應項目是否不相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值不相等。|
|[operator%](../standard-library/valarray-operators.md#op_mod)|取得兩個相等大小 valarray 之對應項目相除的餘數，或 valarray 除以此 valarray 項目類型指定值的餘數，或指定值除以 valarray 的餘數。|
|[operator&](../standard-library/valarray-operators.md#op_amp)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `AND`。|
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `AND`。|
|[operator>](../standard-library/valarray-operators.md#op_gt)|測試一個 valarray 的項目是否大於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於此 valarray 的項目類型指定值。|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|測試一個 valarray 的項目是否大於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元右移。|
|[operator<](../standard-library/valarray-operators.md#op_lt)|測試一個 valarray 的項目是否小於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於指定值。|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|測試一個 valarray 的項目是否小於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|
|[operator<<](../standard-library/valarray-operators.md#op_lt_lt)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元左移。|
|[operator*](../standard-library/valarray-operators.md#op_star)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的乘積。|
|[operator+](../standard-library/valarray-operators.md#op_add)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的和。|
|[operator-](../standard-library/valarray-operators.md#operator-)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的差。|
|[operator/](../standard-library/valarray-operators.md#op_div)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的商。|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|測試兩個大小相等之 valarray 的對應項目是否相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值相等。|
|[operator^](../standard-library/valarray-operators.md#op_xor)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元互斥 `OR`。|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `OR`。|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `OR`。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[gslice 類別](../standard-library/gslice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的多維度切割。|
|[gslice_array 類別](../standard-library/gslice-array-class.md)|可藉由提供 valarray 之一般切割所定義的子集陣列之間的作業，支援一般切割物件的內部、輔助的範本類別。|
|[indirect_array 類別](../standard-library/indirect-array-class.md)|對於指定父代 valarray 索引子集而定義的子集陣列，可藉由提供這些子集之間的作業，支援 valarray 子集物件的內部、輔助的範本類別。|
|[mask_array 類別](../standard-library/mask-array-class.md)|可藉由提供子集之間的作業，以布林運算式指定，並支援父代 valarray 子集物件的內部、輔助的範本類別。|
|[slice 類別](../standard-library/slice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的一維、類似向量的子集。|
|[slice_array 類別](../standard-library/slice-array-class.md)|可藉由提供 valarray 之切割所定義的子集陣列之間的作業，支援切割物件的內部、輔助的範本類別。|
|[valarray 類別](../standard-library/valarray-class.md)|此範本類別描述控制序列的項目型別的物件`Type`會儲存成陣列，專門設計來執行高速的數學運算，針對計算效能最佳化。|

### <a name="specializations"></a>特製化

|||
|-|-|
|[valarray\<bool> 類別](../standard-library/valarray-bool-class.md)|範本類別 valarray 的特製化的版本\<**型別**> 項目型別的**bool**。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
