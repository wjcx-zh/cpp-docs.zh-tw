---
title: remove_extent 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::remove_extent
helpviewer_keywords:
- remove_extent class
- remove_extent
ms.assetid: b9320862-3891-49fc-80bc-571eb2c035cf
ms.openlocfilehash: 1425de12158354c649ec355124f8c255255b29c2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/31/2018
ms.locfileid: "50436382"
---
# <a name="removeextent-class"></a>remove_extent 類別

從陣列類型建立項目類型。

## <a name="syntax"></a>語法

```cpp
template <class T>
struct remove_extent;

template <class T>
using remove_extent_t = typename remove_extent<T>::type;
```

### <a name="parameters"></a>參數

*T*<br/>
要修改的類型。

## <a name="remarks"></a>備註

執行個體`remove_extent<T>`儲存修改的類型是`T1`當*T*的格式`T1[N]`，否則為*T*。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

int main()
    {
    std::cout << "remove_extent_t<int> == "
        << typeid(std::remove_extent_t<int>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5]> == "
        << typeid(std::remove_extent_t<int[5]>).name()
        << std::endl;T
    std::cout << "remove_extent_t<int[5][10]> == "
        << typeid(std::remove_extent_t<int[5][10]>).name()
        << std::endl;
    return (0);
    }
```

```Output
remove_extent_t<int> == int
remove_extent_t<int[5]> == int
remove_extent_t<int[5][10]> == int [10]
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[remove_all_extents 類別](../standard-library/remove-all-extents-class.md)<br/>
