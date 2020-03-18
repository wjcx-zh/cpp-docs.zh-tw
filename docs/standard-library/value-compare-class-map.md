---
title: value_compare 類別 (&lt;map&gt;)
ms.date: 11/04/2016
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
ms.openlocfilehash: 1f872edce6f0114be7c90a8108ba248fd793a989
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447577"
---
# <a name="value_compare-class-ltmapgt"></a>value_compare 類別 (&lt;map&gt;)

提供函式物件，該物件可透過比較對應項目的索引鍵值來比較項目，以判斷項目在對應中的相對順序。

## <a name="syntax"></a>語法

```cpp
class value_compare : public binary_function<value_type, value_type, bool>
{
public:
    bool operator()(const value_type& left, const value_type& right) const;
    value_compare(key_compare pred) : comp(pred);
protected:
    key_compare comp;
};
```

## <a name="remarks"></a>備註

在對應所包含的整個元素 `value_types` 之間 `value_compare` 所提供的比較準則，是由輔助類別結構中個別元素的索引鍵之間的比較所引發。 成員函式運算子會使用類型的物件 `comp` `key_compare` 儲存在 `value_compare` 所提供的函式物件中，以比較兩個專案的排序關鍵字元件。

對於集和多重集而言 (這些是簡單容器，其中索引鍵值和項目值相同)，`value_compare` 相當於 `key_compare`；但對於對應和多重對應則否，因為項目型別 `pair` 的值與項目的索引鍵值不同。

## <a name="example"></a>範例

如需如何宣告和使用 [ 的範例，請參閱 ](../standard-library/map-class.md#value_comp)value_comp`value_compare` 範例。

## <a name="requirements"></a>需求

**標頭：** \<對應 >

**命名空間:** std

## <a name="see-also"></a>另請參閱

[binary_function 結構](../standard-library/binary-function-struct.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)\
[C++ 標準程式庫參考資料](../standard-library/cpp-standard-library-reference.md)
