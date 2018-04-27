---
title: tuple_size 函式 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- tuple_size
- std::tuple_size
- utility/std::tuple_size
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_size
ms.assetid: 73852fc5-eb68-41f1-8379-465cedc2314a
caps.latest.revision: 23
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 647fa1af327055f487d2522d57ee70119f04e627
ms.sourcegitcommit: dd1a509526fa8bb18e97ab7bc7b91cbdb3ec7059
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="tuplesize-class"></a>tuple_size 函式

報告 `tuple` 包含的元素數目。

## <a name="syntax"></a>語法

```cpp
// TEMPLATE STRUCT tuple_size
template <class Tuple>
   struct tuple_size;

// number of elements in array
template <class Elem, size_t Size>
   struct tuple_size<array<Elem, Size>>
      : integral_constant<size_t, Size>;

// size of pair
template <class T1, class T2>
   struct tuple_size<pair<T1, T2>>
      : integral_constant<size_t, 2>

// size of tuple
template <class... Types>
   struct tuple_size<tuple<Types...>>
      : integral_constant<size_t, sizeof...(Types)>;

// size of const tuple
template <class Tuple>
   struct tuple_size<const Tuple>;

// size of volatile tuple
template <class Tuple>
   struct tuple_size<volatile Tuple>;

// size of const volatile tuple
template <class Tuple>
   struct tuple_size<const volatile Tuple>;
```

### <a name="parameters"></a>參數

*Tuple* tuple 的類型。

*Elem*陣列項目的類型。

*大小*陣列的大小。

*T1*的第一個配對成員的類型。

*T2*組的第二個成員的型別。

*型別*tuple 項目類型。

## <a name="remarks"></a>備註

範本類別有一個成員 `value` 是整數常數運算式，其值為 tuple 類型 `Tuple`的範圍。

陣列的樣板特製化有一個成員 `value`，其是值為 `Size` 的整數常數運算式，而該值是陣列的大小。

配對的樣板特製化有一個成員 `value`，其是值為 2 的整數常數運算式。

## <a name="example"></a>範例

```cpp
#include <tuple>
#include <iostream>

using namespace std;

typedef tuple<int, double, int, double> MyTuple;
int main()
{
    MyTuple c0(0, 1.5, 2, 3.7);

    // display contents " 0 1 2 3"
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0);
    cout << " " << get<2>(c0);
    cout << " " << get<3>(c0) << endl;

    // display size " 4"
    cout << " " << tuple_size<MyTuple>::value << endl;
}
```

```Output
 0 1.5 2 3.7
```

## <a name="requirements"></a>需求

**標頭：** \<tuple >**標頭：** \<陣列 > （適用於陣列特製化）**標頭：** \<公用程式 > （適用於組特製化）

**命名空間：** std

## <a name="see-also"></a>另請參閱

[\<tuple>](../standard-library/tuple.md)<br/>
[tuple](../standard-library/tuple-class.md)<br/>
[tuple_element 類別](../standard-library/tuple-element-class-tuple.md)<br/>
