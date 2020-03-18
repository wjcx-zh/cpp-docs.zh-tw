---
title: value_compare 類別
ms.date: 11/04/2016
f1_keywords:
- hash_map/std::value_compare
helpviewer_keywords:
- value_compare class
ms.assetid: c306c5b9-3505-4357-aa6b-216451b951ed
ms.openlocfilehash: d64d51869ca8db1ed42e9d33691f59da4473d8d0
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447573"
---
# <a name="value_compare-class"></a>value_compare 類別

提供函式物件，該物件可透過比較 hash_map 項目的索引鍵值來比較項目，以判斷項目在 hash_map 中的相對順序。

## <a name="syntax"></a>語法

```cpp
class value_compare
    : std::public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(
        const value_type& left,
        const value_type& right) const
    {
        return (comp(left.first, right.first));
    }

protected:
    value_compare(const key_compare& c) : comp (c) { }
    key_compare comp;
};
```

## <a name="remarks"></a>備註

Hash_map 所包含的整個元素 `value_types` 之間 value_compare 所提供的比較準則，是由輔助類別結構的個別元素索引鍵之間的比較引發。 成員函式運算子會使用類型的物件 `comp` `key_compare` 儲存在 value_compare 所提供的函式物件中，以比較兩個專案的排序關鍵字元件。

對於 hash_sets 和 hash_multisets 而言 (這些是簡單容器，其中索引鍵值和項目值相同)，value_compare 相當於 `key_compare`；但對於 hash_maps 和 hash_multimaps 則否，因為項目型別 `pair` 的值與項目的索引鍵值不同。

## <a name="example"></a>範例

如需如何宣告和使用 value_compare 的範例，請參閱 [hash_map::value_comp](../standard-library/hash-map-class.md#value_comp) 範例。

## <a name="requirements"></a>需求

**標頭：** \<hash_map >

**命名空間：** stdext

## <a name="see-also"></a>另請參閱

[binary_function 結構](../standard-library/binary-function-struct.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)
