---
title: is_default_constructible 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_default_constructible
dev_langs:
- C++
helpviewer_keywords:
- is_default_constructible
ms.assetid: dd8f1c44-dae5-4258-891f-c5e048d94092
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 23a361362d574910d21b0031d5687331f8c11dda
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38964251"
---
# <a name="isdefaultconstructible-class"></a>is_default_constructible 類別

測試類型是否有預設建構函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_default_constructible;
```

### <a name="parameters"></a>參數

*T*要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*T*是類別類型具有預設建構函式，否則為 false。 這相當於述詞 `is_constructible<T>`。 型別*T*必須是完整的型別**void**，或是界限未知的陣列。

## <a name="example"></a>範例

```cpp
#include <type_traits>
#include <iostream>

struct Simple
{
    Simple() : val(0) {}
    int val;
};

struct Simple2
{
    Simple2(int v) : val(v) {}
    int val;
};

int main()
{
    std::cout << "is_default_constructible<Simple> == " << std::boolalpha
        << std::is_default_constructible<Simple>::value << std::endl;
    std::cout << "is_default_constructible<Simple2> == " << std::boolalpha
        << std::is_default_constructible<Simple2>::value << std::endl;

    return (0);
}

```

```Output
is_default_constructible<Simple> == true
is_default_constructible<Simple2> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
