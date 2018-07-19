---
title: tuple_element 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- utility/std::tuple_element
dev_langs:
- C++
helpviewer_keywords:
- std::tuple_element
ms.assetid: 4c51a6c1-ce81-462f-8c6c-291d69f2b77c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3ae46a78484a2ee2737f3d949e525ce89d8401cd
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38959065"
---
# <a name="tupleelement-class"></a>tuple_element 類別

包裝 `tuple` 項目。 特製化包裝 `array` 項目和 `pair` 項目。

## <a name="syntax"></a>語法

```cpp
// CLASS tuple_element (find element by index)
template <size_t Index, class Tuple>
   struct tuple_element;

// tuple_element for const
template <size_t Index, class Tuple>
   struct tuple_element<Index, const Tuple>;

// tuple_element for volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, volatile Tuple>;

// tuple_element for const volatile
template <size_t Index, class Tuple>
   struct tuple_element<Index, const volatile Tuple>;

// Helper typedef
template <size_t Index, class Tuple>
   using tuple_element_t = typename tuple_element<Index, Tuple>::type;

// Specialization for arrays
template <size_t Index, class Elem, size_t Size>
   struct tuple_element<Index, array<Elem, Size>>;

// Specializations for pairs
// struct to determine type of element 0 in pair
template <class T1, class T2>
   struct tuple_element<0, pair<T1, T2>>;

// struct to determine type of element 1 in pair
template <class T1, class T2>
   struct tuple_element<1, pair<T1, T2>>;
```

### <a name="parameters"></a>參數

*Tuple*  
指定之項目的索引。

*Tuple*  
Tuple 的類型。

*Elem*  
陣列元素的類型。

*Size*  
陣列的大小。

*T1*  
配對中第一個項目型別。

*T2*  
配對中第二個元素的類型。

## <a name="remarks"></a>備註

此範本類別`tuple_element`具有巢狀的 typedef`type`也就是在索引類型的同義字*Index* tuple 型別*Tuple*。

typedef `tuple_element_t` 是 `tuple_element<Index, Tuple>::type` 的方便別名。

陣列的樣板類別特製化會提供介面給 `array`，當做 `Size` 元素的 tuple，其中每一個都有相同的類型。 每個特製化有巢狀的 typedef`type`也就是類型的同義字*Index*項目`array`，包含保留的任何 const volatile 限定性條件。

`pair` 類型的樣板特製化都提供單一成員 typedef，`type`，也就是在配對中指定位置的元素類型同義字，保留了任何 const 及/或 volatile 限定性條件。 typedef `tuple_element_t` 是 `tuple_element<N, pair<T1, T2>>::type` 的方便別名。

使用[取得函式&lt;公用程式&gt;](../standard-library/utility-functions.md#get)傳回在指定的位置，或指定型別的項目。

## <a name="example"></a>範例

```cpp
#include <tuple>
#include <string>
#include <iostream>

using namespace std;
typedef tuple<int, double, string> MyTuple;

int main() {
    MyTuple c0{ 0, 1.5, "Tail" };

    tuple_element_t<0, MyTuple> val = get<0>(c0); //get by index
    tuple_element_t<1, MyTuple> val2 = get<1>(c0);
    tuple_element_t<2, MyTuple> val3 = get<string>(c0); // get by type

    cout << val << " " << val2 << " " << val3 << endl;
}
```

```Output
0 1.5 Tail
```

## <a name="example"></a>範例

```cpp
#include <array>
#include <iostream>

using namespace std;
typedef array<int, 4> MyArray;

int main()
{
    MyArray c0 { 0, 1, 2, 3 };

    for (const auto& e : c0)
    {
        cout << " " << e;
    }
    cout << endl;

    // display first element " 0"
    tuple_element<0, MyArray>::type val = c0.front();
    cout << " " << val << endl;
}
```

```Output
 0 1 2 3
 0
```

## <a name="example"></a>範例

```cpp
#include <utility>
#include <iostream>

using namespace std;

typedef pair<int, double> MyPair;
int main() {
    MyPair c0(0, 1.333);

    // display contents " 0 1"
    cout << " " << get<0>(c0);
    cout << " " << get<1>(c0) << endl;

    // display first element " 0" by index
    tuple_element<0, MyPair>::type val = get<0>(c0);
    cout << " " << val;

    // display second element by type
    tuple_element<1, MyPair>::type val2 = get<double>(c0);
    cout << " " << val2 << endl;
}
```

```Output
 0 1.333
 0 1.333
```

## <a name="requirements"></a>需求

**標頭：** \<tuple >**標頭：** \<陣列 > （用於陣列特製化）**標頭：** \<公用程式 > （用於配對特製化） **命名空間：** std

## <a name="see-also"></a>另請參閱

[tuple ](../standard-library/tuple-class.md)<br/>
