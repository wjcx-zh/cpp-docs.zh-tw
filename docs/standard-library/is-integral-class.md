---
title: is_integral 類別
ms.date: 11/04/2016
f1_keywords:
- type_traits/std::is_integral
helpviewer_keywords:
- is_integral class
- is_integral
ms.assetid: fe9279d0-4495-4e88-bf23-153cc6602397
ms.openlocfilehash: c7d0d8b8572c26bfa75b9fab81900c0ae21fb932
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/10/2018
ms.locfileid: "51520695"
---
# <a name="isintegral-class"></a>is_integral 類別

測試類型是否為整數。

## <a name="syntax"></a>語法

```cpp
template <class Ty>
struct is_integral;
```

### <a name="parameters"></a>參數

*Ty*<br/>
要查詢的類型。

## <a name="remarks"></a>備註

如果型別述詞的執行個體保留 true 的型別*Ty*是其中一個整數類資料類型，或`cv-qualified`形式的其中一個整數型別，否則為 false。

整數類資料類型是其中一個**bool**， **char**， **unsigned char**， **char&lt;3**， **wchar_t**， **簡短**， **unsigned short**， **int**，**不帶正負號的 int**，**長**，與**unsigned long**。 此外，以提供它們的編譯器，整數型別可以是其中一個**長長**， **unsigned long long**， **__int64**，和**不帶正負號的 __int64**.

## <a name="example"></a>範例

```cpp
// std__type_traits__is_integral.cpp
// compile with: /EHsc
#include <type_traits>
#include <iostream>

struct trivial
    {
    int val;
    };

int main()
    {
    std::cout << "is_integral<trivial> == " << std::boolalpha
        << std::is_integral<trivial>::value << std::endl;
    std::cout << "is_integral<int> == " << std::boolalpha
        << std::is_integral<int>::value << std::endl;
    std::cout << "is_integral<float> == " << std::boolalpha
        << std::is_integral<float>::value << std::endl;

    return (0);
    }
```

```Output
is_integral<trivial> == false
is_integral<int> == true
is_integral<float> == false
```

## <a name="requirements"></a>需求

**標頭：**\<type_traits>

**命名空間：** std

## <a name="see-also"></a>另請參閱

[<type_traits>](../standard-library/type-traits.md)<br/>
[is_enum 類別](../standard-library/is-enum-class.md)<br/>
[is_floating_point 類別](../standard-library/is-floating-point-class.md)<br/>
