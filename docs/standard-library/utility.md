---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: eaae94bcffcda6e113001dd7070bcc80e7c14d09
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/24/2019
ms.locfileid: "68458072"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

可定義 C++ 標準程式庫類型、函式與運算子，並協助建構及管理成對的物件，當需要將兩個物件視為一體時相當實用。

## <a name="requirements"></a>需求

**標頭：** \<utility>

**命名空間：** std

## <a name="remarks"></a>備註

C++ 標準程式庫中很廣泛地運用配對。 做為引數並傳回不同函式的值，以及做為容器的項目型別，例如 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)時，都需要用到配對。 \<map> 會自動納入 \<utility> 標頭，以協助管理其索引及成對的鍵/值型別項目。

> [!NOTE]
> 公用程式 > 標頭會使用`#include <initializer_list>`語句。 \< 它也會參考`class tuple`在元組\<> 中定義的。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|||
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|基本數值轉換的浮點格式。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|包裝 `pair` 項目類型的類別。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|類別，其中包裝 `pair` 項目計數。|

### <a name="objects"></a>物件

|||
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)||
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)||
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)||
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)||

### <a name="functions"></a>函式

|||
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|傳回類型。|
|[declval](../standard-library/utility-functions.md#declval)|縮寫運算式評估。|
|[exchange](../standard-library/utility-functions.md#exchange)|將新值指派給物件, 並傳回其舊值。|
|[forward](../standard-library/utility-functions.md#forward)|保留引數的參考類型 (可能是 `lvalue` 或 `rvalue`)，避免被完整轉寄遮蔽。|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|函式，其可從 `pair` 物件取得項目。|
|[make_pair](../standard-library/utility-functions.md#make_pair)|範本協助程式函式，可用以建構 `pair` 類型的物件，而其中的元件類型會以傳遞為參數的資料類型做為基礎。|
|[move](../standard-library/utility-functions.md#move)|傳回已傳入的引數，做為 `rvalue` 參考。|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[swap](../standard-library/utility-functions.md#swap)|交換兩個 `pair` 物件的項目。|
|[to_chars](../standard-library/utility-functions.md#to_chars)|將值轉換成字元字串。|

### <a name="operators"></a>運算子

|||
|-|-|
|[operator!=](../standard-library/utility-operators.md#op_neq)|測試成對運算子左側的物件是否不等於右側的物件。|
|[operator==](../standard-library/utility-operators.md#op_eq_eq)|測試成對運算子左側的物件是否等於右側的物件。|
|[operator\<](../standard-library/utility-operators.md#op_lt)|測試成對運算子左側的物件是否小於右側的物件。|
|[operator\<=](../standard-library/utility-operators.md#op_gt_eq)|測試成對運算子左側的物件是否小於或等於右側的物件。|
|[operator>](../standard-library/utility-operators.md#op_gt)|測試成對運算子左側的物件是否大於右側的物件。|
|[operator>=](../standard-library/utility-operators.md#op_gt_eq)|測試成寺運算子左側的物件是否大於或等於右側的物件。|

### <a name="structs"></a>結構

|||
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|用於的`from_chars`結構。|
|[identity](../standard-library/identity-structure.md)|一種提供類型定義來作為範本參數的結構。|
|[in_place_t](../standard-library/in-place-t-struct.md)|也包含結構`in_place_type_t`和`in_place_index_t`。|
|[integer_sequence](../standard-library/integer-sequence-class.md)|表示整數序列。|
|[pair](../standard-library/pair-structure.md)|類型，其提供可將兩個物件視為單一物件的功能。|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|用來保留個別的函式和函數多載的類型。|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|用於的`to_chars`結構。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
