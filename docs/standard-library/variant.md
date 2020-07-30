---
title: '&lt;variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 6074c80b20ae0c69d34768bc16d7aaae16c99579
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87232816"
---
# <a name="ltvariantgt"></a>&lt;variant&gt;

Variant 物件會保存並管理值。 如果變數包含值，該值的類型必須是指定給 variant 的其中一個樣板引數類型。 這些範本引數稱為替代方案。

## <a name="requirements"></a>需求

**標頭：**\<variant>

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>操作員

|||
|-|-|
|[operator = =](../standard-library/forward-list-operators.md#op_eq_eq)|測試運算子左邊的 variant 物件是否等於右邊的 variant 物件。。|
|[operator！ =](../standard-library/forward-list-operators.md#op_neq)|測試運算子左邊的 variant 物件是否不等於右邊的 variant 物件。。|
|[運算子<](../standard-library/forward-list-operators.md#op_lt)|測試運算子左邊的 variant 物件是否小於右邊的 variant 物件。」|
|[運算子<=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件是否小於或等於右邊的 variant 物件。（& a）|
|[運算子>](../standard-library/forward-list-operators.md#op_gt)|測試運算子左邊的 variant 物件是否大於右邊的 variant 物件。」|
|[運算子>=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件是否大於或等於右邊的 variant 物件。（& a）|

### <a name="functions"></a>函式

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|取得物件的變體。|
|[get_if](../standard-library/variant-functions.md#get_if)|取得物件的 variant （如果有的話）。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|**`true`** 如果有 variant 存在，則傳回。|
|[調換](../standard-library/variant-functions.md#swap)|交換**variant**。|
|[流覽](../standard-library/variant-functions.md#visit)|移至下一個**variant**。|

### <a name="classes"></a>類別

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|所擲回的物件會向 variant 物件的值報告不正確存取權。|
|[variant](../standard-library/variant.md)|物件，用來存放其中一個替代類型的值，或不包含任何值。|

### <a name="structs"></a>結構

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|將 variant 類型設為預設可建構之 variant 的替代類型。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|協助變體物件。|
|[variant_size](../standard-library/variant-size-structure.md)|協助變體物件。|

### <a name="objects"></a>物件

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
