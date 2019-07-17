---
title: '&lt;map&gt;'
ms.date: 11/04/2016
f1_keywords:
- <map>
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
ms.openlocfilehash: 96ca19b2562c3f145555c3c1b1d8db4fc700ed91
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243316"
---
# <a name="ltmapgt"></a>&lt;map&gt;

定義容器樣板類別對應和多重對應，以及其支援的樣板。

## <a name="requirements"></a>需求

**標頭：** \<map>

**命名空間：** std

> [!NOTE]
> \<對應 > 程式庫也會使用`#include <initializer_list>`陳述式。

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|對應版本|多重對應版本|說明|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|測試運算子左邊的對應或多重對應物件是否不等於右邊的對應或多重對應物件。|
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|測試運算子左邊的對應或多重對應物件是否小於右邊的對應或多重對應物件。|
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|測試運算子左邊的對應或多重對應物件是否小於或等於右邊的對應或多重對應物件。|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|測試運算子左邊的對應或多重對應物件是否等於右邊的對應或多重對應物件。|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|測試運算子左邊的對應或多重對應物件是否大於右邊的對應或多重對應物件。|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|測試運算子左邊的對應或多重對應物件是否大於或等於右邊的對應或多重對應物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|對應版本|多重對應版本|說明|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|交換兩個對應或多重對應的項目。|

### <a name="classes"></a>類別

|||
|-|-|
|[value_compare 類別](../standard-library/value-compare-class-map.md)|提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。|
|[map 類別](../standard-library/map-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的唯一索引鍵。|
|[multimap 類別](../standard-library/multimap-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的索引鍵，而且這些索引鍵不需要具有唯一的值。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
