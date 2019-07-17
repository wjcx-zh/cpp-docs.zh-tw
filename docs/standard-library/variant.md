---
title: '&lt;Variant&gt;'
ms.date: 04/04/2019
f1_keywords:
- <variant>
helpviewer_keywords:
- <variant>
ms.openlocfilehash: 7a812ccc3c8cb2a660c01ad2b17ea75b5d5c9542
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68268440"
---
# <a name="ltvariantgt"></a>&lt;Variant&gt;

變數的物件會保存，並管理值。 如果變數保留值的類型必須是指定給變數的範本引數類型的其中一個值。 這些範本引數所呼叫的替代方案。

## <a name="requirements"></a>需求

**標頭：** \<variant >

**命名空間：** std

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|||
|-|-|
|[operator==](../standard-library/forward-list-operators.md#op_eq_eq)|測試運算子左邊的 variant 物件等於右邊的 variant 物件。|
|[operator!=](../standard-library/forward-list-operators.md#op_neq)|測試運算子左邊的 variant 物件是否不等於右邊的 variant 物件。|
|[operator<](../standard-library/forward-list-operators.md#op_lt)|測試運算子左邊的 variant 物件是否小於右邊的 variant 的物件。|
|[operator<=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件小於或等於 variant 的物件，在右邊。|
|[operator>](../standard-library/forward-list-operators.md#op_gt)|測試運算子左邊的 variant 物件大於右邊的 variant 的物件。|
|[operator>=](../standard-library/forward-list-operators.md#op_lt_eq)|測試運算子左邊的 variant 物件是否大於或等於右邊的 variant 物件。|

### <a name="functions"></a>函式

|||
|-|-|
|[get](../standard-library/variant-functions.md#get)|取得物件的變體。|
|[get_if](../standard-library/variant-functions.md#get_if)|若有的話，請取得物件的變體。|
|[holds_alternative](../standard-library/variant-functions.md#holds_alternative)|傳回 **，則為 true**有變化。|
|[swap](../standard-library/variant-functions.md#swap)|交換**variant**。|
|[請瀏覽](../standard-library/variant-functions.md#visit)|移至下一步**variant**。|

### <a name="classes"></a>類別

|||
|-|-|
|[bad_variant_access](../standard-library/bad-variant-access-class.md)|擲回以報告無效的存取，變數物件的值的物件。|
|[Variant](../standard-library/variant.md)|為物件保存其替代的型別，或沒有值的值。|

### <a name="structs"></a>結構

|||
|-|-|
|[hash](../standard-library/hash-structure.md)||
|[monostate](../standard-library/monostate-structure.md)|變數將變數類型的預設建構替代類型。|
|[uses_allocator](../standard-library/uses-allocator-structure.md)||
|[variant_alternative](../standard-library/variant-alternative-structure.md)|可協助 variant 的物件。|
|[variant_size](../standard-library/variant-size-structure.md)|可協助 variant 的物件。|

### <a name="objects"></a>物件

|||
|-|-|
|[variant_npos](../standard-library/variant-functions.md#variant_npos)||

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)
