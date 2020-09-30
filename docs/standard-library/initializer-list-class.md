---
title: initializer_list 類別
description: C + + 標準程式庫中 initializer_list 類別的參考，由 Microsoft 在 Visual Studio 中執行。
ms.date: 01/28/2020
f1_keywords:
- initializer_list/std::initializer_list::initializer_list
- initializer_list/std::initializer_list::begin
- initializer_list/std::initializer_list::end
- initializer_list/std::initializer_list::size
ms.assetid: 1f2c0ff4-5636-4f79-b008-e75426e3d2ab
helpviewer_keywords:
- std::initializer_list::initializer_list
- std::initializer_list::begin
- std::initializer_list::end
- std::initializer_list::size
ms.openlocfilehash: 232855fbcac1e4df9af7cf956fda80201326a401
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/29/2020
ms.locfileid: "91504637"
---
# <a name="initializer_list-class"></a>initializer_list 類別

提供對項目的陣列之存取，其中每個成員都有指定的類型。

## <a name="syntax"></a>語法

```cpp
template <class Type>
class initializer_list
```

### <a name="parameters"></a>參數

*類型*\
要存放在 `initializer_list` 中的項目資料類型。

## <a name="remarks"></a>備註

可以使用括號初始設定式清單建構 `initializer_list`：

```cpp
initializer_list<int> i1{ 1, 2, 3, 4 };
```

每當函式簽章需要 `initializer_list` 時，編譯器會將以大括號括住且具有同質項目的初始設定式清單轉換至 `initializer_list`。 如需使用的詳細資訊 `initializer_list` ，請參閱[統一初始化和委派](../cpp/initializing-classes-and-structs-without-constructors-cpp.md)函式

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[initializer_list](#initializer_list)|建構類型 `initializer_list` 的物件。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|`value_type`|`initializer_list` 中的項目類型。|
|`reference`|類型，提供在 `initializer_list` 中之項目的參考。|
|`const_reference`|類型，提供在 `initializer_list` 中之項目的常數參考。|
|`size_type`|代表 `initializer_list` 中項目數的類型。|
|`iterator`|提供 `initializer_list` 之迭代器的類型。|
|`const_iterator`|提供 `initializer_list` 之常數迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[開始](#begin)|傳回 `initializer_list` 中第一個項目的指標。|
|[end](#end)|傳回超出 `initializer_list` 中最後一個項目的項目指標。|
|[size](#size)|傳回 `initializer_list` 中項目的數目。|

## <a name="requirements"></a>需求

**標頭：**\<initializer_list>

**命名空間：** std

## <a name="initializer_listbegin"></a><a name="begin"></a> initializer_list：： begin

傳回 `initializer_list` 中第一個項目的指標。

```cpp
constexpr const InputIterator* begin() const noexcept;
```

### <a name="return-value"></a>傳回值

指向 `initializer_list` 第一個項目的指標。 如果此清單是空的，則該清單開頭和結尾的指標相同。

## <a name="initializer_listend"></a><a name="end"></a> initializer_list：： end

傳回超出 `initializer list` 中最後一個項目的項目指標。

```cpp
constexpr const InputIterator* end() const noexcept;
```

### <a name="return-value"></a>傳回值

超出清單中最後一個項目的項目指標。 如果清單是空的，它會與清單中第一個元素的指標相同。

## <a name="initializer_listinitializer_list"></a><a name="initializer_list"></a> initializer_list：： initializer_list

建構類型 `initializer_list` 的物件。

```cpp
constexpr initializer_list() noexcept;
initializer_list(const InputIterator First, const InputIterator Last);
```

### <a name="parameters"></a>參數

*第一*\
要複製的元素範圍中第一個元素的位置。

*最後*\
超出要複製之元素範圍的第一個元素的位置。

### <a name="remarks"></a>備註

`initializer_list` 的基礎為指定類型的物件陣列。 複製會 `initializer_list` 建立指向相同物件之清單的第二個實例; 不會複製基礎物件。

### <a name="example"></a>範例

```cpp
// initializer_list_class.cpp
// compile with: /EHsc
#include <initializer_list>
#include <iostream>

int main()
{
    using namespace std;
    // Create an empty initializer_list c0
    initializer_list <int> c0;

    // Create an initializer_list c1 with 1 element
    initializer_list <int> c1{ 3 };

    // Create an initializer_list c2 with 5 elements
    initializer_list <int> c2{ 5, 4, 3, 2, 1 };

    // Create a copy, initializer_list c3, of initializer_list c2
    initializer_list <int> c3(c2);

    // Create a initializer_list c4 by copying the range c3[ first,  last)
    const int* c3_ptr = c3.begin();
    c3_ptr++;
    c3_ptr++;
    initializer_list <int> c4(c3.begin(), c3_ptr);

    // Move initializer_list c4 to initializer_list c5
    initializer_list <int> c5(move(c4));

    cout << "c1 =";
    for (auto c : c1)
        cout << " " << c;
    cout << endl;

    cout << "c2 =";
    for (auto c : c2)
        cout << " " << c;
    cout << endl;

    cout << "c3 =";
    for (auto c : c3)
        cout << " " << c;
    cout << endl;

    cout << "c5 =";
    for (auto c : c5)
        cout << " " << c;
    cout << endl;
}
```

```Output
c1 = 3
c2 = 5 4 3 2 1
c3 = 5 4 3 2 1
c5 = 5 4
```

## <a name="initializer_listsize"></a><a name="size"></a> initializer_list：： size

傳回清單中項目的數目。

```cpp
constexpr size_t size() const noexcept;
```

### <a name="return-value"></a>傳回值

清單中項目的數目。

## <a name="see-also"></a>另請參閱

[<forward_list>](../standard-library/forward-list.md)
