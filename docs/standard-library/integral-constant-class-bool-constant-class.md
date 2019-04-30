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
ms.openlocfilehash: f7b9217560bc94c536a7c819276266fd16fa4b07
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404867"
---
# <a name="integralconstant-class-boolconstant-class"></a>integral_constant 類別、bool_constant 類別

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

*T*<br/>
常數的類型。

*v*<br/>
常數的值。

## <a name="remarks"></a>備註

以整數類型 *T* 和該類型的值 *v* 將 `integral_constant` 範本類別特製化時，此類別會代表持有該整數類型之常數並具有指定值的物件。 名為 `type` 的成員是所產生範本特製化類型的別名，而 `value` 成員則持有用來建立特製化的值 *v*。

`bool_constant`範本類別是的明確部分特製化`integral_constant`使用**bool**作為*T*引數。

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

[<type_traits>](../standard-library/type-traits.md)<br/>
[false_type](../standard-library/type-traits-typedefs.md#false_type)<br/>
[true_type](../standard-library/type-traits-typedefs.md#true_type)<br/>
