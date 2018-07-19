---
title: value_compare 類別 (&lt;map&gt;) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- std::value_compare
- std.value_compare
- map/std::value_compare
- value_compare
dev_langs:
- C++
helpviewer_keywords:
- std::value_compare
ms.assetid: ea97c1d0-04b2-4d42-8d96-23522c04cc41
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 46f8d00877aa4147e4b3e4ec2a6a23b70d8154c8
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38965844"
---
# <a name="valuecompare-class-ltmapgt"></a>value_compare 類別 (&lt;map&gt;)

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

所提供的比較準則`value_compare`之間`value_types`整個對應所包含的項目引發從個別的項目，透過輔助類別建構的索引鍵之間的比較。 成員函式運算子會使用物件`comp`型別的`key_compare`所提供的函式物件中儲存`value_compare`來比較兩個項目的排序鍵元件。

對於集和多重集而言 (這些是簡單容器，其中索引鍵值和項目值相同)，`value_compare` 相當於 `key_compare`；但對於對應和多重對應則否，因為項目型別 `pair` 的值與項目的索引鍵值不同。

## <a name="example"></a>範例

如需如何宣告和使用 [ 的範例，請參閱 ](../standard-library/map-class.md#value_comp)value_comp`value_compare` 範例。

## <a name="requirements"></a>需求

**標頭：**\<map>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[binary_function 結構](../standard-library/binary-function-struct.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[C++ 標準程式庫參考](../standard-library/cpp-standard-library-reference.md)<br/>
