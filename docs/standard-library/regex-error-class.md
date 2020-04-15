---
title: regex_error 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
ms.openlocfilehash: f8f3c88c1b203ed7fcea148843fa99590e27b888
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81331862"
---
# <a name="regex_error-class"></a>regex_error 類別

回報錯誤的 basic_regex 物件。

## <a name="syntax"></a>語法

```cpp
class regex_error
: public std::runtime_error
```

## <a name="remarks"></a>備註

此類別描述為了回報建構或使用 `basic_regex` 物件時所發生的錯誤，所擲回的例外狀況物件。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[regex_error](#regex_error)|建構物件。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[代碼](#code)|傳回錯誤碼。|

## <a name="requirements"></a>需求

**標頭︰** \<regex>

**命名空間：** std

## <a name="example"></a>範例

```cpp
// std__regex__regex_error.cpp
// compile with: /EHsc
#include <regex>
#include <iostream>

int main()
    {
    std::regex_error paren(std::regex_constants::error_paren);

    try
        {
        std::regex rx("(a");
        }
    catch (const std::regex_error& rerr)
        {
        std::cout << "regex error: "
            << (rerr.code() == paren.code() ? "unbalanced parentheses" : "")
            << std::endl;
        }
    catch (...)
        {
        std::cout << "unknown exception" << std::endl;
        }

    return (0);
    }
```

```Output
regex error: unbalanced parentheses
```

## <a name="regex_errorcode"></a><a name="code"></a>regex_error:代碼

傳回錯誤碼。

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>備註

成員函式會傳回傳遞給物件建構函式的值。

## <a name="regex_errorregex_error"></a><a name="regex_error"></a>regex_error::regex_error

建構物件。

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>參數

*錯誤*\
錯誤碼。

### <a name="remarks"></a>備註

構造函數構造保存值*誤差*的物件。

## <a name="see-also"></a>另請參閱

[\<正則>](../standard-library/regex.md)\
[regex_constants類](../standard-library/regex-constants-class.md)\
[\<正規表示式>函數](../standard-library/regex-functions.md)\
[regex_iterator類](../standard-library/regex-iterator-class.md)\
[\<正則>運算子](../standard-library/regex-operators.md)\
[regex_token_iterator類](../standard-library/regex-token-iterator-class.md)\
[regex_traits類](../standard-library/regex-traits-class.md)\
[\<正則>型態](../standard-library/regex-typedefs.md)
