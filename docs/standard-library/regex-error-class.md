---
title: regex_error 類別 | Microsoft Docs
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- regex/std::regex_error
- regex/std::regex_error::code
dev_langs:
- C++
helpviewer_keywords:
- regex_error class
ms.assetid: 3333a1a3-ca6f-4612-84b2-1b4c7e3db5a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7358af41e1a7172daec619bec3e701ff4541fd0c
ms.sourcegitcommit: 27b5712badd09a09c499d887e2e4cf2208a28603
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2018
ms.locfileid: "44384978"
---
# <a name="regexerror-class"></a>regex_error 類別

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

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[程式碼](#code)|傳回錯誤碼。|

## <a name="requirements"></a>需求

**標頭︰**\<regex>

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

## <a name="code"></a>  regex_error::code

傳回錯誤碼。

```cpp
regex_constants::error_code code() const;
```

### <a name="remarks"></a>備註

成員函式會傳回傳遞給物件建構函式的值。

## <a name="regex_error"></a>  regex_error::regex_error

建構物件。

```cpp
regex_error(regex_constants::error_code error);
```

### <a name="parameters"></a>參數

*error*<br/>
錯誤碼。

### <a name="remarks"></a>備註

建構函式會建構一個物件，會保留值*錯誤*。

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)<br/>
[regex_constants 類別](../standard-library/regex-constants-class.md)<br/>
[\<regex> 函式](../standard-library/regex-functions.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
