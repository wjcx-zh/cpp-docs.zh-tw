---
title: integral_constant 類別、bool_constant 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::integral_constant
- XTR1COMMON/std::integral_constant
- type_traits/std::bool_constant
- XTR1COMMON/std::bool_constant
helpviewer_keywords:
- std::integral_constant [C++]
- std::bool_constant [C++]
ms.assetid: 11c002c6-4d31-4042-9341-f2543f43e108
ms.openlocfilehash: 30e00fdc166b4a6f2db64a3552a3bb87335c7e32
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87233141"
---
# <a name="integral_constant-class-bool_constant-class"></a>integral_constant 類別、bool_constant 類別

從類型及值建立整數常數。

## <a name="syntax"></a>語法

```cpp
template<class T, T v>
struct integral_constant {
   static constexpr T value = v;
   typedef T value_type;
   typedef integral_constant<T, v> type;
   constexpr operator value_type() const noexcept;
   constexpr value_type operator()() const noexcept;
   };
```

### <a name="parameters"></a>參數

*而已*\
常數的類型。

*&*\
常數的值。

## <a name="remarks"></a>備註

`integral_constant`當使用整數型*別 T*和該型別的值*v*來特殊化時，類別樣板代表的物件會保存具有指定值之整數型別的常數。 名為 `type` 的成員是所產生範本特製化類型的別名，而 `value` 成員則持有用來建立特製化的值 *v*。

`bool_constant`類別樣板是 `integral_constant` 使用 **`bool`** 做為*T*引數的明確部分特製化。

## <a name="example"></a>範例

```cpp
// std__type_traits__integral_constant.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "integral_constant<int, 5> == "
        << std::integral_constant<int, 5>::value << std::endl;
    std::cout << "integral_constant<bool, false> == " << std::boolalpha
        << std::integral_constant<bool, false>::value << std::endl;

    return (0);
    }
```

```Output
integral_constant<int, 5> == 5
integral_constant<bool, false> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)\
[false_type](../standard-library/type-traits-typedefs.md#false_type)\
[true_type](../standard-library/type-traits-typedefs.md#true_type)
