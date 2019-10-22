---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: 00ca476816213d38b3c50c64e0978e65ac1a5ea1
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687939"
---
# <a name="lthash_setgt"></a>&lt;hash_set&gt;

> [!NOTE]
> 這個標頭已淘汰。 替代方案是 [<unordered_set>](../standard-library/unordered-set.md)。

定義容器類別範本 hash_set 和 hash_multiset 及其支援的範本。

## <a name="syntax"></a>語法

```cpp
#include <hash_set>
```

## <a name="remarks"></a>備註

### <a name="operators"></a>運算子

|Hash_set 版本|Hash_multiset 版本|描述|
|-----------------------|----------------------------|-----------------|
|[operator!= (hash_set)](../standard-library/hash-set-operators.md#op_neq)|[operator!= (hash_multiset)](../standard-library/hash-set-operators.md#op_neq)|測試運算子左邊的 hash_set 或 hash_multiset 物件是否不等於右邊的 hash_set 或 hash_multiset 物件。|
|[operator== (hash_set)](../standard-library/hash-set-operators.md#op_eq_eq)|[operator== (hash_multiset)](../standard-library/hash-set-operators.md#op_eq_eq)|測試運算子左邊的 hash_set 或 hash_multiset 物件是否等於右邊的 hash_set 或 hash_multiset 物件。|

### <a name="specialized-template-functions"></a>特製化樣板函式

|Hash_set 版本|Hash_multiset 版本|描述|
|-----------------------|----------------------------|-----------------|
|[swap (hash_set)](../standard-library/hash-set-functions.md#swap)|[swap (hash_multiset)](../standard-library/hash-set-functions.md#swap_hash_multiset)|交換兩個 hash_sets 或 hash_multisets 的元素。|

### <a name="classes"></a>類別

|執行個體|描述|
|-|-|
|[hash_compare 類別](../standard-library/hash-compare-class.md)|描述可由任何雜湊關聯容器（hash_map、hash_multimap、hash_set 或 hash_multiset）用來做為預設 `Traits` 參數物件的物件，以排序及雜湊其包含的元素。|
|[hash_set 類別](../standard-library/hash-set-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|
|[hash_multiset 類別](../standard-library/hash-multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|

## <a name="see-also"></a>請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)
