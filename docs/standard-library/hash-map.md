---
title: '&lt;hash_map&gt;'
ms.date: 01/18/2018
f1_keywords:
- <hash_map>
- std::<hash_map>
helpviewer_keywords:
- hash_map header
ms.openlocfilehash: e586a933c2a80b7e611bcd4b4714e300eb21a0ad
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689565"
---
# <a name="lthash_mapgt"></a>&lt;hash_map&gt;

> [!NOTE]
> 這個標頭已淘汰。 替代方式是[\<unordered_map >](unordered-map.md)。

定義容器類別範本 hash_map 和 hash_multimap 及其支援的範本。

## <a name="syntax"></a>語法

```
#include <hash_map>
```

### <a name="operators"></a>運算子

|Hash_map 版本|Hash_multimap 版本|描述|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_map)](hash-map-operators.md#op_neq)|[operator！ = （hash_multimap）](hash-map-operators.md#op_neq_mm)|測試運算子左邊的 hash_map 或 hash_multimap 物件是否不等於右邊的 hash_map 或 hash_multimap 物件。|
|[operator== (hash_map)](hash-map-operators.md#op_eq_eq)|[operator== (hash_multimap)](hash-map-operators.md#op_eq_eq_mm)|測試運算子左邊的 hash_map 或 hash_multimap 物件是否等於右邊的 hash_map 或 hash_multimap 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|Hash_map 版本|Hash_multimap 版本|描述|
|-----------------------|----------------------------|-----------------|
|[swap (hash_map)](hash-map-class.md#swap)|[swap (hash_multimap)](hash-multimap-class.md#swap)|交換兩個 hash_maps 或 hash_multimaps 的項目。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[hash_compare 類別](hash-compare-class.md)|描述可由任何雜湊關聯容器（hash_map、hash_multimap、hash_set 或 hash_multiset）用來做為預設 `Traits` 參數物件的物件，以排序及雜湊其包含的元素。|
|[value_compare 類別](value-compare-class.md)|提供函式物件，該物件可透過比較 hash_map 項目的索引鍵值來比較項目，以判斷項目在 hash_map 中的相對順序。|
|[hash_map 類別](hash-map-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 (其值唯一) 和相關聯資料值的配對。|
|[hash_multimap 類別](hash-multimap-class.md)|用以儲存及快速擷取集合中的資料，其中每個項目為具有排序鍵 (其值可重複) 和相關聯資料值的配對。|

## <a name="requirements"></a>需求

**標頭：** \<hash_map>

**命名空間：** stdext

## <a name="see-also"></a>請參閱

[標頭檔參考](cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](cpp-standard-library-reference.md)
