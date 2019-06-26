---
title: regex_constants 類別
ms.date: 09/10/2018
f1_keywords:
- regex/std::regex_constants
- regex/std::regex_constants::error_collate
- regex/std::regex_constants::error_ctype
- regex/std::regex_constants::error_escape
- regex/std::regex_constants::error_backref
- regex/std::regex_constants::error_brack
- regex/std::regex_constants::error_paren
- regex/std::regex_constants::error_brace
- regex/std::regex_constants::error_badbrace
- regex/std::regex_constants::error_range
- regex/std::regex_constants::error_space
- regex/std::regex_constants::error_badrepeat
- regex/std::regex_constants::error_complexity
- regex/std::regex_constants::error_stack
- regex/std::regex_constants::error_parse
- regex/std::regex_constants::error_syntax
- regex/std::regex_constants::match_default
- regex/std::regex_constants::match_not_bol
- regex/std::regex_constants::match_not_eol
- regex/std::regex_constants::match_not_bow
- regex/std::regex_constants::match_not_eow
- regex/std::regex_constants::match_any
- regex/std::regex_constants::match_not_null
- regex/std::regex_constants::match_continuous
- regex/std::regex_constants::match_prev_avail
- regex/std::regex_constants::format_default
- regex/std::regex_constants::format_sed
- regex/std::regex_constants::format_no_copy
- regex/std::regex_constants::format_first_only
- regex/std::regex_constants::ECMAScript
- regex/std::regex_constants::basic
- regex/std::regex_constants::extended
- regex/std::regex_constants::awk
- regex/std::regex_constants::grep
- regex/std::regex_constants::egrep
- regex/std::regex_constants::icase
- regex/std::regex_constants::nosubs
- regex/std::regex_constants::optimize
- regex/std::regex_constants::collate
helpviewer_keywords:
- std::regex_constants [C++]
- std::regex_constants [C++], error_collate
- std::regex_constants [C++], error_ctype
- std::regex_constants [C++], error_escape
- std::regex_constants [C++], error_backref
- std::regex_constants [C++], error_brack
- std::regex_constants [C++], error_paren
- std::regex_constants [C++], error_brace
- std::regex_constants [C++], error_badbrace
- std::regex_constants [C++], error_range
- std::regex_constants [C++], error_space
- std::regex_constants [C++], error_badrepeat
- std::regex_constants [C++], error_complexity
- std::regex_constants [C++], error_stack
- std::regex_constants [C++], error_parse
- std::regex_constants [C++], error_syntax
- std::regex_constants [C++], match_default
- std::regex_constants [C++], match_not_bol
- std::regex_constants [C++], match_not_eol
- std::regex_constants [C++], match_not_bow
- std::regex_constants [C++], match_not_eow
- std::regex_constants [C++], match_any
- std::regex_constants [C++], match_not_null
- std::regex_constants [C++], match_continuous
- std::regex_constants [C++], match_prev_avail
- std::regex_constants [C++], format_default
- std::regex_constants [C++], format_sed
- std::regex_constants [C++], format_no_copy
- std::regex_constants [C++], format_first_only
- std::regex_constants [C++], ECMAScript
- std::regex_constants [C++], basic
- std::regex_constants [C++], extended
- std::regex_constants [C++], awk
- std::regex_constants [C++], grep
- std::regex_constants [C++], egrep
- std::regex_constants [C++], icase
- std::regex_constants [C++], nosubs
- std::regex_constants [C++], optimize
- std::regex_constants [C++], collate
ms.assetid: 4a69c0ba-c46d-46e4-bd29-6f4efb805f26
ms.openlocfilehash: b657dbc5ae537e15f6638ffbd3594cd52b644f3b
ms.sourcegitcommit: 8bb2bea1384b290b7570b01608a86c7488ae7a02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/26/2019
ms.locfileid: "67400784"
---
# <a name="regexconstants-namespace"></a>regex_constants 命名空間

規則運算式旗標的命名空間。

## <a name="syntax"></a>語法

```cpp
namespace regex_constants {
    enum syntax_option_type;
    enum match_flag_type;
    enum error_type;
}
```

## <a name="remarks"></a>備註

`regex_constants` 命名空間會封裝幾個旗標類型及其關聯的旗標值。

|||
|-|-|
|[error_type](#error_type)|規則運算式語法錯誤報告的旗標。|
|[match_flag_type](#match_flag_type)|規則運算式比對選項的旗標。|
|[syntax_option_type](#syntax_option_type)|用於選取語法選項的旗標。|

## <a name="requirements"></a>需求

**標頭︰** \<regex>

**命名空間：** std

## <a name="error_type"></a>  regex_constants::error_type

規則運算式語法錯誤報告的旗標。

```cpp
enum error_type
    {    // identify error
    error_collate,
    error_ctype,
    error_escape,
    error_backref,
    error_brack,
    error_paren,
    error_brace,
    error_badbrace,
    error_range,
    error_space,
    error_badrepeat,
    error_complexity,
    error_stack,
    error_parse,
    error_syntax
    };
```

### <a name="remarks"></a>備註

此類型為列舉類型，描述可以保留錯誤旗標的物件。 不同的旗標值為：

`error_backref` -- 運算式包含無效的反向參考

`error_badbrace` -- 運算式在 { } 運算式中包含無效計數

`error_badrepeat` -- 重複運算式 (大部分內容中含 '* '、''、'+'、' {' 其中之一) 之前沒有運算式

`error_brace` -- 運算式包含不對稱的 '{' 或 '}'

`error_brack` -- 運算式包含不對稱的 '[' 或 ']'

`error_collate` -- 運算式包含無效的定序項目名稱

`error_complexity` -- 嘗試比對因為太複雜而失敗

`error_ctype` -- 運算式包含無效的字元類別名稱

`error_escape` -- 運算式包含無效的逸出序列

`error_paren` -- 運算式包含不對稱的 '(' 或 ')'

`error_parse` -- 無法剖析運算式

`error_range` -- 運算式包含無效的字元範圍規範

`error_space` -- 剖析規則運算式失敗，因為沒有足夠的資源可供使用

`error_stack` -- 嘗試比對失敗，因為沒有足夠的記憶體可供使用

`error_syntax` -- 無法剖析語法錯誤

`error_backref` -- 運算式包含無效的反向參考

## <a name="match_flag_type"></a>  regex_constants::match_flag_type

規則運算式比對選項的旗標。

```cpp
enum match_flag_type
    {    // specify matching and formatting rules
    match_default = 0x0000,
    match_not_bol = 0x0001,
    match_not_eol = 0x0002,
    match_not_bow = 0x0004,
    match_not_eow = 0x0008,
    match_any = 0x0010,
    match_not_null = 0x0020,
    match_continuous = 0x0040,
    match_prev_avail = 0x0100,
    format_default = 0x0000,
    format_sed = 0x0400,
    format_no_copy = 0x0800,
    format_first_only = 0x1000,
    _Match_not_null = 0x2000
    };
```

### <a name="remarks"></a>備註

此類型是位元遮罩類型，描述根據規則運算式比對文字序列時所要使用的選項，以及取代文字時所要使用的格式旗標。 這些選項可以搭配 `|`使用。

比對選項包括：

`match_default`

`match_not_bol` -- 不會將目標序列中的第一個位置視為行首

`match_not_eol` -- 不會將目標序列中超過結尾的位置視為行尾

`match_not_bow` -- 不會將目標序列中的第一個位置視為字首

`match_not_eow` -- 不會將目標序列中超過結尾的位置視為字尾

`match_any` -- 如果可能有多個相符項目，則可接受所有相符項目

`match_not_null` -- 不會將空的子序列視為相符項目

`match_continuous` -- 只會從目標序列開頭搜尋相符項目

`match_prev_avail` -- `--first` 是有效的迭代器；如果已設定，則會忽略 `match_not_bol` 和 `match_not_bow`

格式旗標包括：

`format_default` -- 使用 ECMAScript 格式規則

`format_sed` -- 使用 sed 格式規則

`format_no_copy` -- 不會複製不符合規則運算式的文字

`format_first_only` -- 只會搜尋第一個相符項目

## <a name="syntax_option_type"></a>  regex_constants::syntax_option_type

用於選取語法選項的旗標。

```cpp
enum syntax_option_type
    {    // specify RE syntax rules
    ECMAScript = 0x01,
    basic = 0x02,
    extended = 0x04,
    awk = 0x08,
    grep = 0x10,
    egrep = 0x20,
    _Gmask = 0x3F,

    icase = 0x0100,
    nosubs = 0x0200,
    optimize = 0x0400,
    collate = 0x0800
    };
```

### <a name="remarks"></a>備註

此類型是位元遮罩類型，用於描述編譯規則運算式時，所要使用的語言規範和語法修飾詞。 這些選項可以搭配 `|`使用。 一次只能使用一個語言規範。

語言規範如下：

`ECMAScript` -- 編譯成 ECMAScript

`basic` -- 編譯成 BRE

`extended` -- 編譯成 ERE

`awk` -- 編譯成 awk

`grep` -- 編譯成 grep

`egrep` -- 編譯成 egrep

語法修飾詞如下：

`icase` -- 使所有相符項目皆不區分大小寫

`nosubs` -- 實作不需要持續追蹤擷取群組的內容

`optimize` -- 實作應強調比對速度，而不是規則運算式的編譯速度

`collate` -- 使所有相符項目皆區分地區設定

## <a name="see-also"></a>另請參閱

[\<regex>](../standard-library/regex.md)<br/>
[regex_error 類別](../standard-library/regex-error-class.md)<br/>
[\<regex> 函式](../standard-library/regex-functions.md)<br/>
[regex_iterator 類別](../standard-library/regex-iterator-class.md)<br/>
[\<regex> 運算子](../standard-library/regex-operators.md)<br/>
[regex_token_iterator 類別](../standard-library/regex-token-iterator-class.md)<br/>
[regex_traits 類別](../standard-library/regex-traits-class.md)<br/>
[\<regex> typedefs](../standard-library/regex-typedefs.md)<br/>
