---
title: '&lt;hash_set&gt;'
ms.date: 11/04/2016
f1_keywords:
- <hash_set>
- std::<hash_set>
helpviewer_keywords:
- hash_set header
ms.assetid: 6b556967-c808-4869-9b4d-f9e030864435
ms.openlocfilehash: a9ed3cf90c4650683eac1c198a8b57614e96d759
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50449452"
---
# <a name="lthashsetgt"></a>&lt;hash_set&gt;

> [!NOTE]
> 這個標頭已淘汰。 替代方案是 [<unordered_set>](../standard-library/unordered-set.md)。

定義容器樣板類別 hash_set 和 hash_multiset，以及其支援的樣板。

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

|類別|描述|
|-|-|
|[hash_compare 類別](../standard-library/hash-compare-class.md)|描述可由任一雜湊關聯容器的物件 — hash_map、 hash_multimap、 hash_set 或 hash_multiset — 預設值為`Traits`參數物件，以便排序與雜湊所包含的元素。|
|[hash_set 類別](../standard-library/hash-set-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|
|[hash_multiset 類別](../standard-library/hash-multiset-class.md)|用於在集合中儲存和擷取資料，集合中包含的元素值是唯一的，並且會作為索引鍵值。|

## <a name="see-also"></a>另請參閱

[標頭檔參考](../standard-library/cpp-standard-library-header-files.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
