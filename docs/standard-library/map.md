---
title: '&lt;map&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <map>
dev_langs:
- C++
helpviewer_keywords:
- map header
ms.assetid: bbf76680-7362-456e-88fa-ecda93561b6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ac523342cc175721b9c1ef33a3d8ac4cad83033b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="ltmapgt"></a>&lt;map&gt;

定義容器樣板類別對應和多重對應，以及其支援的樣板。

## <a name="syntax"></a>語法

```cpp
#include <map>

```

## <a name="members"></a>成員

### <a name="operators"></a>運算子

|對應版本|多重對應版本|描述|
|-----------------|----------------------|-----------------|
|[operator!= (map)](../standard-library/map-operators.md#op_neq)|[operator!= (multimap)](../standard-library/map-operators.md#op_neq)|測試運算子左邊的對應或多重對應物件是否不等於右邊的對應或多重對應物件。|
|[operator< (map)](../standard-library/map-operators.md#op_eq_eq)|[operator< (multimap)](../standard-library/map-operators.md#op_eq_eq)|測試運算子左邊的對應或多重對應物件是否小於右邊的對應或多重對應物件。|
|[operator<= (map)](../standard-library/map-operators.md#op_lt)|[operator\<= (multimap)](../standard-library/map-operators.md#op_lt)|測試運算子左邊的對應或多重對應物件是否小於或等於右邊的對應或多重對應物件。|
|[operator== (map)](../standard-library/map-operators.md#op_eq_eq)|[operator== (multimap)](../standard-library/map-operators.md#op_eq_eq_multimap)|測試運算子左邊的對應或多重對應物件是否等於右邊的對應或多重對應物件。|
|[operator> (map)](../standard-library/map-operators.md#op_gt)|[operator> (multimap)](../standard-library/map-operators.md#op_gt_multimap)|測試運算子左邊的對應或多重對應物件是否大於右邊的對應或多重對應物件。|
|[operator>= (map)](../standard-library/map-operators.md#op_gt_eq)|[operator>= (multimap)](../standard-library/map-operators.md#op_gt_eq_multimap)|測試運算子左邊的對應或多重對應物件是否大於或等於右邊的對應或多重對應物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|對應版本|多重對應版本|描述|
|-----------------|----------------------|-----------------|
|[swap (map)](../standard-library/map-functions.md#swap)|[swap (multimap)](../standard-library/map-functions.md#swap_multimap)|交換兩個對應或多重對應的項目。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[value_compare 類別](../standard-library/value-compare-class-map.md)|提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。|
|[map 類別](../standard-library/map-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的唯一索引鍵。|
|[multimap 類別](../standard-library/multimap-class.md)|用於儲存及擷取集合中的資料，集合中的每個項目都有用來自動排序資料的索引鍵，而且這些索引鍵不需要具有唯一的值。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
