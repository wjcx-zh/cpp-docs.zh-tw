---
title: '&lt;locale&gt; 函式'
ms.date: 11/04/2016
f1_keywords:
- locale/std::has_facet
- locale/std::isalnum
- locale/std::isalpha
- locale/std::iscntrl
- locale/std::isdigit
- locale/std::isgraph
- locale/std::islower
- locale/std::isprint
- locale/std::ispunct
- locale/std::isspace
- locale/std::isupper
- locale/std::isxdigit
- locale/std::tolower
- locale/std::toupper
- locale/std::use_facet
ms.assetid: b06c1ceb-33a7-48d3-8d4b-2714bbb27f14
helpviewer_keywords:
- std::has_facet [C++]
- std::isalnum [C++]
- std::isalpha [C++]
- std::iscntrl [C++]
- std::isdigit [C++]
- std::isgraph [C++]
- std::islower [C++]
- std::isprint [C++]
- std::ispunct [C++]
- std::isspace [C++]
- std::isupper [C++]
- std::isxdigit [C++]
- std::tolower [C++]
- std::toupper [C++]
- std::use_facet [C++]
ms.openlocfilehash: a1e81fe28976e914f90a441ff97027f411b05738
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224808"
---
# <a name="ltlocalegt-functions"></a>&lt;locale&gt; 函式

||||
|-|-|-|
|[has_facet](#has_facet)|[isalnum](#isalnum)|[isalpha](#isalpha)|
|[iscntrl](#iscntrl)|[isdigit](#isdigit)|[isgraph](#isgraph)|
|[islower](#islower)|[isprint](#isprint)|[ispunct](#ispunct)|
|[isspace](#isspace)|[isupper](#isupper)|[isxdigit](#isxdigit)|
|[tolower](#tolower)|[toupper](#toupper)|[use_facet](#use_facet)|

## <a name="has_facet"></a><a name="has_facet"></a>has_facet

測試特定的 facet 是否在指定的地區設定中儲存。

```cpp
template <class Facet>
bool has_facet(const locale& Loc);
```

### <a name="parameters"></a>參數

*Loc*\
要測試是否有 facet 存在的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果地區設定的 facet 已針對進行測試，則為;**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式可用來在呼叫 `use_facet` 之前，先檢查地區設定中是否有列出非強制性 facet，以避免因 facet 不存在而擲回例外狀況。

### <a name="example"></a>範例

```cpp
// locale_has_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result = has_facet <ctype<char> > ( loc );
   cout << result << endl;
}
```

```Output
1
```

## <a name="isalnum"></a><a name="isalnum"></a>isalnum

測試地區設定中的項目是否為字母或數字字元。

```cpp
template <class CharType>
bool isalnum(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的英數字元元素。

*Loc*\
包含要測試之英數字元元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是英數位元，則為，**`false`** 如果不是，則為。

### <a name="example"></a>範例

```cpp
// locale_isalnum.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalnum ( 'L', loc);
   bool result2 = isalnum ( '@', loc);
   bool result3 = isalnum ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphanumeric." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphanumeric." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphanumeric." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphanumeric." << endl;
}
```

```Output
The character 'L' in the locale is alphanumeric.
The character '@' in the locale is  not alphanumeric.
The character '3' in the locale is alphanumeric.
```

## <a name="isalpha"></a><a name="isalpha"></a>isAlpha

測試地區設定中的元素是否為字母字元。

```cpp
template <class CharType>
bool isalpha(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之字母元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是英文字母，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **Alpha**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_isalpha.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isalpha ( 'L', loc);
   bool result2 = isalpha ( '@', loc);
   bool result3 = isalpha ( '3', loc);

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not alphabetic." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not alphabetic." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "alphabetic." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not alphabetic." << endl;
}
```

## <a name="iscntrl"></a><a name="iscntrl"></a>iscntrl

測試地區設定中的項目是否為控制字元。

```cpp
template <class CharType>
bool iscntrl(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是控制字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **cntrl**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_iscntrl.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = iscntrl ( 'L', loc );
   bool result2 = iscntrl ( '\n', loc );
   bool result3 = iscntrl ( '\t', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a control character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a control character." << endl;

   if ( result2 )
      cout << "The character-set 'backslash-n' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale\n is "
           << " not a control character." << endl;

   if ( result3 )
      cout << "The character-set 'backslash-t' in the locale\n is "
           << "a control character." << endl;
   else
      cout << "The character-set 'backslash-n' in the locale \n is "
           << " not a control character." << endl;
}
```

## <a name="isdigit"></a><a name="isdigit"></a>isdigit

測試地區設定中的項目是否為數字字元。

```cpp
template <class CharType>
bool isdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是數位字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：：**數位**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_is_digit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isdigit ( 'L', loc );
   bool result2 = isdigit ( '@', loc );
   bool result3 = isdigit ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a numeric character." << endl;

   if ( result2 )
      cout << "The character '@' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '@' in the locale is "
           << " not a numeric character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a numeric character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a numeric character." << endl;
}
```

## <a name="isgraph"></a><a name="isgraph"></a>isgraph

測試地區設定中的項目是否為英數字元或標點符號字元。

```cpp
template <class CharType>
bool isgraph(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是英數位元或標點符號字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **graph**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_is_graph.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isgraph ( 'L', loc );
   bool result2 = isgraph ( '\t', loc );
   bool result3 = isgraph ( '.', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;

   if ( result2 )
      cout << "The character 'backslash-t' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is\n "
           << "not an alphanumeric or punctuation character." << endl;

   if ( result3 )
      cout << "The character '.' in the locale is\n "
           << "an alphanumeric or punctuation character." << endl;
   else
      cout << "The character '.' in the locale is\n "
           << " not an alphanumeric or punctuation character." << endl;
}
```

## <a name="islower"></a><a name="islower"></a>islower

測試地區設定中的項目是否為小寫。

```cpp
template <class CharType>
bool islower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是小寫字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **lower**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_islower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = islower ( 'L', loc );
   bool result2 = islower ( 'n', loc );
   bool result3 = islower ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a lowercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a lowercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a lowercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a lowercase character." << endl;
}
```

## <a name="isprint"></a><a name="isprint"></a>isprint

測試地區設定中的項目是否為可列印的字元。

```cpp
template <class CharType>
bool isprint(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是可列印的;**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **print**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_isprint.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );

   bool result1 = isprint ( 'L', loc );
   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a printable character." << endl;

   bool result2 = isprint( '\t', loc );
   if ( result2 )
      cout << "The character 'backslash-t' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-t' in the locale is "
           << " not a printable character." << endl;

   bool result3 = isprint( '\n', loc );
   if ( result3 )
      cout << "The character 'backslash-n' in the locale is "
           << "a printable character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a printable character." << endl;
}
```

## <a name="ispunct"></a><a name="ispunct"></a>ispunct

測試地區設定中的項目是否為標點符號字元。

```cpp
template <class CharType>
bool ispunct(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是標點符號字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) `<` [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **punct**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_ispunct.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = ispunct ( 'L', loc );
   bool result2 = ispunct ( ';', loc );
   bool result3 = ispunct ( '*', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a punctuation character." << endl;

   if ( result2 )
      cout << "The character ';' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character ';' in the locale is "
           << " not a punctuation character." << endl;

   if ( result3 )
      cout << "The character '*' in the locale is "
           << "a punctuation character." << endl;
   else
      cout << "The character '*' in the locale is "
           << " not a punctuation character." << endl;
}
```

## <a name="isspace"></a><a name="isspace"></a>isspace

測試地區設定中的項目是否為空白字元。

```cpp
template <class CharType>
bool isspace(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是空白字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **space**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_isspace.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isspace ( 'L', loc );
   bool result2 = isspace ( '\n', loc );
   bool result3 = isspace ( ' ', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a whitespace character." << endl;

   if ( result2 )
      cout << "The character 'backslash-n' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character 'backslash-n' in the locale is "
           << " not a whitespace character." << endl;

   if ( result3 )
      cout << "The character ' ' in the locale is "
           << "a whitespace character." << endl;
   else
      cout << "The character ' ' in the locale is "
           << " not a whitespace character." << endl;
}
```

## <a name="isupper"></a><a name="isupper"></a>isupper

測試地區設定中的元素是否為大寫。

```cpp
template <class CharType>
bool isupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是大寫字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **upper**， `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_isupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isupper ( 'L', loc );
   bool result2 = isupper ( 'n', loc );
   bool result3 = isupper ( '3', loc );

   if ( result1 )
      cout << "The character 'L' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'L' in the locale is "
           << " not a uppercase character." << endl;

   if ( result2 )
      cout << "The character 'n' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character 'n' in the locale is "
           << " not a uppercase character." << endl;

   if ( result3 )
      cout << "The character '3' in the locale is "
           << "a uppercase character." << endl;
   else
      cout << "The character '3' in the locale is "
           << " not a uppercase character." << endl;
}
```

## <a name="isxdigit"></a><a name="isxdigit"></a>isxdigit

測試地區設定中的項目是否為用來表示十六進位數字的字元。

```cpp
template <class CharType>
bool isxdigit(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要測試的元素。

*Loc*\
包含要測試之元素的地區設定。

### <a name="return-value"></a>傳回值

**`true`** 如果測試的元素是用來表示十六進位數位的字元，則為，**`false`** 如果不是，則為。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [is](../standard-library/ctype-class.md#is)（ **ctype** \< **CharType**> ：： **xdigit**， `Ch` ）。

十六進位數字會使用以 16 為底數的方式來表示數字，其中是使用數字 0 到 9 再加上不區分大小寫的字母 A 到 F，來表示十進位數字 0 到 15。

### <a name="example"></a>範例

```cpp
// locale_isxdigit.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>

using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = isxdigit ( '5', loc );
   bool result2 = isxdigit ( 'd', loc );
   bool result3 = isxdigit ( 'q', loc );

   if ( result1 )
      cout << "The character '5' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character '5' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result2 )
      cout << "The character 'd' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'd' in the locale is "
           << " not a hexidecimal digit-character." << endl;

   if ( result3 )
      cout << "The character 'q' in the locale is "
           << "a hexidecimal digit-character." << endl;
   else
      cout << "The character 'q' in the locale is "
           << " not a hexidecimal digit-character." << endl;
}
```

## <a name="tolower"></a><a name="tolower"></a>tolower

將字元轉換為小寫。

```cpp
template <class CharType>
CharType tolower(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要轉換為小寫的字元。

*Loc*\
包含要轉換之字元的地區設定。

### <a name="return-value"></a>傳回值

已轉換為小寫的字元。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [tolower](../standard-library/ctype-class.md#tolower)（ `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = tolower ( 'H', loc );
   cout << "The lower case of 'H' in the locale is: "
        << result1 << "." << endl;
   char result2 = tolower ( 'h', loc );
   cout << "The lower case of 'h' in the locale is: "
        << result2 << "." << endl;
   char result3 = tolower ( '$', loc );
   cout << "The lower case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="toupper"></a><a name="toupper"></a>toupper

將字元轉換為大寫。

```cpp
template <class CharType>
CharType toupper(CharType Ch, const locale& Loc)
```

### <a name="parameters"></a>參數

*頻道*\
要轉換為大寫的字元。

*Loc*\
包含要轉換之字元的地區設定。

### <a name="return-value"></a>傳回值

已轉換為大寫的字元。

### <a name="remarks"></a>備註

此範本函式會傳回[use_facet](../standard-library/locale-functions.md#use_facet) <  [ctype](../standard-library/ctype-class.md) \< **CharType**> > （ `Loc` ）。 [toupper](../standard-library/ctype-class.md#toupper)（ `Ch` ）。

### <a name="example"></a>範例

```cpp
// locale_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   char result1 = toupper ( 'h', loc );
   cout << "The upper case of 'h' in the locale is: "
        << result1 << "." << endl;
   char result2 = toupper ( 'H', loc );
   cout << "The upper case of 'H' in the locale is: "
        << result2 << "." << endl;
   char result3 = toupper ( '$', loc );
   cout << "The upper case of '$' in the locale is: "
        << result3 << "." << endl;
}
```

## <a name="use_facet"></a><a name="use_facet"></a>use_facet

傳回儲存在地區設定中指定之類型的 facet 的參考。

```cpp
template <class Facet>
const Facet& use_facet(const locale& Loc);
```

### <a name="parameters"></a>參數

*Loc*\
包含所要參考之 facet 類型的常數地區設定。

### <a name="return-value"></a>傳回值

對 locale 引數內所包含之 `Facet` 類別 facet 的參考。

### <a name="remarks"></a>備註

只要有任何一個包含 facet 的地區設定複本存在，此範本函式所傳回對 facet 的參考就會保持有效。 如果 locale 引數中未列出任何這類 `Facet` 類別的 facet 物件，此函式就會擲回 `bad_cast` 例外狀況。

### <a name="example"></a>範例

```cpp
// locale_use_facet.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );
   bool result1 = use_facet<ctype<char> > ( loc1 ).is(
   ctype_base::alpha, 'a'
);
   bool result2 = use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!'
   );

   if ( result1 )
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if ( result2 )
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;
}
```

```Output
The character 'a' in locale loc1 is alphabetic.
The character '!' in locale loc2 is not alphabetic.
```

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)
