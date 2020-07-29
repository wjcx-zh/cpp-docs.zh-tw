---
title: '&lt;utility&gt;'
ms.date: 11/04/2016
f1_keywords:
- <utility>
helpviewer_keywords:
- utility header
ms.assetid: c4491103-5da9-47a1-9c2b-ed8bc64b0599
ms.openlocfilehash: 1beade28ceec0f1552def4bc70c2e95e6b2aa24d
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87215435"
---
# <a name="ltutilitygt"></a>&lt;utility&gt;

可定義 C++ 標準程式庫類型、函式與運算子，並協助建構及管理成對的物件，當需要將兩個物件視為一體時相當實用。

## <a name="requirements"></a>需求

**標頭：**\<utility>

**命名空間：** std

## <a name="remarks"></a>備註

C++ 標準程式庫中很廣泛地運用配對。 做為引數並傳回不同函式的值，以及做為容器的項目型別，例如 [map 類別](../standard-library/map-class.md)和 [multimap 類別](../standard-library/multimap-class.md)時，都需要用到配對。 \<utility>標頭會自動包含在 \<map> 中，以協助管理其索引鍵/值組類型元素。

> [!NOTE]
> \<utility>標頭會使用語句 `#include <initializer_list>` 。 它也會參考 `class tuple` 中所定義的 \<tuple> 。

## <a name="members"></a>成員

### <a name="classes"></a>類別

|類型|Description|
|-|-|
|[chars_format](../standard-library/chars-format-class.md)|基本數值轉換的浮點格式。|
|[tuple_element](../standard-library/tuple-element-class-tuple.md)|包裝 `pair` 項目類型的類別。|
|[tuple_size](../standard-library/tuple-size-class-tuple.md)|類別，其中包裝 `pair` 項目計數。|

### <a name="objects"></a>物件

|[範本]|說明|
|-|-|
|[index_sequence](../standard-library/utility-functions.md#index_sequence)|為通用案例定義的別名範本，其中 `T` 為`std::size_t`  |
|[index_sequence_for](../standard-library/utility-functions.md#index_sequence_for)|協助程式別名範本，可將任何類型參數套件轉換成相同長度的索引順序|
|[make_index_sequence](../standard-library/utility-functions.md#make_index_sequence)| 協助程式別名範本，可簡化類型的建立 `std::index_sequence` 。 |
|[make_integer_sequence](../standard-library/utility-functions.md#make_integer_sequence)|協助程式別名範本，可簡化類型的建立 `std::integer_sequence` 。|

### <a name="functions"></a>函式

|函式|說明|
|-|-|
|[as_const](../standard-library/utility-functions.md#asconst)|傳回類型。|
|[declval](../standard-library/utility-functions.md#declval)|縮寫運算式評估。|
|[固定匯率](../standard-library/utility-functions.md#exchange)|將新值指派給物件，並傳回其舊值。|
|[邁出](../standard-library/utility-functions.md#forward)|保留引數的參考類型 (可能是 `lvalue` 或 `rvalue`)，避免被完整轉寄遮蔽。|
|[from_chars](../standard-library/utility-functions.md#from_chars)||
|[get](../standard-library/utility-functions.md#get)|函式，其可從 `pair` 物件取得項目。|
|[make_pair](../standard-library/utility-functions.md#make_pair)|範本協助程式函式，可用以建構 `pair` 類型的物件，而其中的元件類型會以傳遞為參數的資料類型做為基礎。|
|[move](../standard-library/utility-functions.md#move)|傳回已傳入的引數，做為 `rvalue` 參考。|
|[move_if_noexcept](../standard-library/utility-functions.md#moveif)||
|[調換](../standard-library/utility-functions.md#swap)|交換兩個 `pair` 物件的項目。|
|[to_chars](../standard-library/utility-functions.md#to_chars)|將值轉換成字元字串。|

### <a name="operators"></a>運算子

|運算子|說明|
|-|-|
|[operator！ =](../standard-library/utility-operators.md#op_neq)|測試成對運算子左側的物件是否不等於右側的物件。|
|[operator = =](../standard-library/utility-operators.md#op_eq_eq)|測試成對運算子左側的物件是否等於右側的物件。|
|[操作\<](../standard-library/utility-operators.md#op_lt)|測試成對運算子左側的物件是否小於右側的物件。|
|[操作\<=](../standard-library/utility-operators.md#op_gt_eq)|測試成對運算子左側的物件是否小於或等於右側的物件。|
|[運算子>](../standard-library/utility-operators.md#op_gt)|測試成對運算子左側的物件是否大於右側的物件。|
|[運算子>=](../standard-library/utility-operators.md#op_gt_eq)|測試成寺運算子左側的物件是否大於或等於右側的物件。|

### <a name="structs"></a>結構

|結構|描述|
|-|-|
|[from_chars_result](../standard-library/from-chars-result-structure.md)|用於的結構 `from_chars` 。|
|[身分識別](../standard-library/identity-structure.md)|一種提供類型定義來作為範本參數的結構。|
|[in_place_t](../standard-library/in-place-t-struct.md)|也包含結構 `in_place_type_t` 和 `in_place_index_t` 。|
|[integer_sequence](../standard-library/integer-sequence-class.md)|表示整數序列。|
|[對](../standard-library/pair-structure.md)|類型，其提供可將兩個物件視為單一物件的功能。|
|[piecewise_construct_t](../standard-library/piecewise-construct-t-structure.md)|用來保留個別的函式和函數多載的類型。|
|[to_chars_result](../standard-library/to-chars-result-structure.md)|用於的結構 `to_chars` 。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
