---
title: is_polymorphic 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_polymorphic
helpviewer_keywords:
- is_polymorphic class
- is_polymorphic
ms.assetid: 4e1704db-d6f9-4154-a100-0ba02a373f20
ms.openlocfilehash: 8d9846f03db60cdad88fccc04ba520eeb935dc33
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51521631"
---
# <a name="ispolymorphic-class"></a>is_polymorphic 類別

測試類型是否有虛擬函式。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_polymorphic;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是類別，宣告或繼承虛擬函式，否則為 false。

## <a name="example"></a>範例

```cpp
// std__type_traits__is_polymorphic.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

struct throws
    {
    throws() throw(int)
        {
        }

    throws(const throws&) throw(int)
        {
        }

    throws& operator=(const throws&) throw(int)
        {
        }

    virtual ~throws()
        {
        }

    int val;
    };

int main()
    {
    std::cout << "is_polymorphic<trivial> == " << std::boolalpha
        << std::is_polymorphic<trivial>::value << std::endl;
    std::cout << "is_polymorphic<throws> == " << std::boolalpha
        << std::is_polymorphic<throws>::value << std::endl;

    return (0);
    }
```

```Output
is_polymorphic<trivial> == false
is_polymorphic<throws> == true
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_abstract 類別](../standard-library/is-abstract-class.md)<br/>
