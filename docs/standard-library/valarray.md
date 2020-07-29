---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: eb782b0d16c4bc826da4ea9291756f34ca0eaf29
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215409"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

定義類別樣板 valarray 和許多支援的類別範本和函式。

## <a name="requirements"></a>需求

**標頭：**\<valarray>

**命名空間：** std

> [!NOTE]
> 連結 \<valarray> 庫使用 ' #include <initializer_list> ' 語句。

## <a name="remarks"></a>備註

這些類別樣板和函式在改善效能方面，允許不尋常的緯度。 具體而言，任何傳回類型 `valarray<T1>` 的函式都可能會傳回其他類型 T2 的物件。 在此情況下，接受類型的一或多個引數的任何函式都 `valarray<T2>` 必須具有接受這些引數任意組合的多載，而且每個函式都會取代為 T2 類型的引數。

## <a name="members"></a>成員

### <a name="functions"></a>函式

|||
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的絕對值相等。|
|[acos](../standard-library/valarray-functions.md#acos)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反餘弦值相等。|
|[asin](../standard-library/valarray-functions.md#asin)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正弦值相等。|
|[atan](../standard-library/valarray-functions.md#atan)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的反正切主值相等。|
|[atan2](../standard-library/valarray-functions.md#atan2)|傳回 valarray，而常數及 valarray 項目組合指定之笛卡兒座標分量的反正切值會與其中的項目相等。|
|[起點](../standard-library/valarray-functions.md#begin)||
|[纜](../standard-library/valarray-functions.md#cos)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的餘弦值相等。|
|[cosh](../standard-library/valarray-functions.md#cosh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲餘弦值相等。|
|[成品](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然指數值相等。|
|[日誌](../standard-library/valarray-functions.md#log)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的自然對數值相等。|
|[log10](../standard-library/valarray-functions.md#log10)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的常用對數值 (底數為 10 的對數) 相等。|
|[pow](../standard-library/valarray-functions.md#pow)|在輸入的 valarray 項目和常數上運作，傳回 valarray，其中的項目等於指定基底以指定指數自乘的乘冪，而該基底由輸入的 valarray 之項目指定或由常數指定，且該指數由輸入的 valarray 或常數指定。|
|[sin](../standard-library/valarray-functions.md#sin)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正弦值相等。|
|[sinh](../standard-library/valarray-functions.md#sinh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正弦值相等。|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的平方根相等。|
|[調換](../standard-library/valarray-functions.md#swap)||
|[相切](../standard-library/valarray-functions.md#tan)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的正切值相等。|
|[tanh](../standard-library/valarray-functions.md#tanh)|在輸入的 valarray 項目上運作，傳回 valarray ，其中的項目和輸入的 valarray 項目的雙曲正切值相等。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator！ =](../standard-library/valarray-operators.md#op_neq)|測試兩個大小相等之 valarray 的對應項目是否不相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值不相等。|
|[操作](../standard-library/valarray-operators.md#op_mod)|取得兩個相等大小 valarray 之對應項目相除的餘數，或 valarray 除以此 valarray 項目類型指定值的餘數，或指定值除以 valarray 的餘數。|
|[運算子&](../standard-library/valarray-operators.md#op_amp)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `AND`。|
|[運算子&&](../standard-library/valarray-operators.md#op_amp_amp)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `AND`。|
|[運算子>](../standard-library/valarray-operators.md#op_gt)|測試一個 valarray 的項目是否大於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於此 valarray 的項目類型指定值。|
|[運算子>=](../standard-library/valarray-operators.md#op_gt_eq)|測試一個 valarray 的項目是否大於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|
|[運算子>>](../standard-library/valarray-operators.md#op_gt_gt)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元右移。|
|[運算子<](../standard-library/valarray-operators.md#op_lt)|測試一個 valarray 的項目是否小於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或小於指定值。|
|[運算子<=](../standard-library/valarray-operators.md#op_lt_eq)|測試一個 valarray 的項目是否小於或等於一個大小相等的 valarray 之項目，或測試 valarray 的所有項目是否大於或等於、小於或等於指定值。|
|[運算子<<](../standard-library/valarray-operators.md#op_lt_lt)|依位置的指定數目或依第二個 valarray 指定的項目數量，將 valarray 的每個項目之位元左移。|
|[操作](../standard-library/valarray-operators.md#op_star)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的乘積。|
|[運算子 +](../standard-library/valarray-operators.md#op_add)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的和。|
|[操作](../standard-library/valarray-operators.md#operator-)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的差。|
|[操作](../standard-library/valarray-operators.md#op_div)|取得兩個相同大小 valarray 對應項目之間、或 valarray 和該 valarray 的項目類型指定值之間項目的商。|
|[operator = =](../standard-library/valarray-operators.md#op_eq_eq)|測試兩個大小相等之 valarray 的對應項目是否相等，或測試 valarray 的所有項目是否都和 valarray 的項目類型指定值相等。|
|[運算子 ^](../standard-library/valarray-operators.md#op_xor)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元互斥 `OR`。|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|取得兩個相同大小 valarray 項目之間、或 valarray 和該項目類型指定值之間的位元 `OR`。|
|[運算子&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|取得兩個相同大小 valarray 項目之間、或 valarray 和該 valarray 的項目類型指定值之間的邏輯 `OR`。|

### <a name="classes"></a>類別

|||
|-|-|
|[gslice 類別](../standard-library/gslice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的多維度切割。|
|[gslice_array 類別](../standard-library/gslice-array-class.md)|內部的輔助類別樣板，透過在 valarray 的一般配量所定義的子集陣列之間提供作業，以支援一般配量物件。|
|[indirect_array 類別](../standard-library/indirect-array-class.md)|內部的輔助類別樣板，藉由指定父 valarray 的索引子集，在定義的子集陣列之間提供作業，藉此支援屬於 valarray 子集的物件。|
|[mask_array 類別](../standard-library/mask-array-class.md)|一種內部的輔助類別樣板，支援以布林運算式指定之父 valarray 子集的物件，方法是提供子集陣列之間的作業。|
|[配量類別](../standard-library/slice-class.md)|valarray 的一個公用程式類別，用來定義 valarray 的一維、類似向量的子集。|
|[slice_array 類別](../standard-library/slice-array-class.md)|內部的輔助類別樣板，藉由在 valarray 的配量所定義的子集陣列之間提供作業，以支援配量物件。|
|[valarray 類別](../standard-library/valarray-class.md)|類別樣板描述一個物件，它會控制一系列類型的專案 `Type` ，這些專案會儲存為數組，並專為執行高速的數學運算而設計，並針對計算效能優化。|

### <a name="specializations"></a>特製化

|||
|-|-|
|[valarray \<bool> 類別](../standard-library/valarray-bool-class.md)|類別樣板的特製化版本會 valarray \<**Type**> 至類型的元素 **`bool`** 。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
