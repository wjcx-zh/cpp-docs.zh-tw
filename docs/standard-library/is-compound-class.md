---
title: is_compound 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- type_traits/std::is_compound
dev_langs:
- C++
helpviewer_keywords:
- is_compound class
- is_compound
ms.assetid: bdad1167-cf3f-4f37-8321-62a5df159ead
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91132492ab6173d9d462eeb74d6393dce41f6833
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/11/2018
ms.locfileid: "38961587"
---
# <a name="iscompound-class"></a>is_compound 類別

測試指定的類型是否不是基本。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_compound;
```

### <a name="parameters"></a>參數

*Ty*要查詢的類型。

## <a name="remarks"></a>備註

類型述詞的執行個體**假**如果的型別*Ty*是一個基本類型 (亦即，如果[is_fundamental](../standard-library/is-fundamental-class.md)\<Ty > 保存**true**);否則，它會保存 **，則為 true**。 因此，述詞**真**如果*Ty*是陣列類型、 函式類型的指標**void**或物件或函式、 參考、 類別、 聯集、 列舉型別，或非靜態類別成員的指標或*cv 限定*形式的其中一個。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_compound.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_compound<trivial> == " << std::boolalpha
        << std::is_compound<trivial>::value << std::endl;
    std::cout << "is_compound<int[]> == " << std::boolalpha
        << std::is_compound<int[]>::value << std::endl;
    std::cout << "is_compound<int()> == " << std::boolalpha
        << std::is_compound<int()>::value << std::endl;
    std::cout << "is_compound<int&> == " << std::boolalpha
        << std::is_compound<int&>::value << std::endl;
    std::cout << "is_compound<void *> == " << std::boolalpha
        << std::is_compound<void *>::value << std::endl;
    std::cout << "is_compound<int> == " << std::boolalpha
        << std::is_compound<int>::value << std::endl;

    return (0);
    }

```

```Output
is_compound<trivial> == true
is_compound<int[]> == true
is_compound<int()> == true
is_compound<int&> == true
is_compound<void *> == true
is_compound<int> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_class 類別](../standard-library/is-class-class.md)<br/>
