---
title: moneypunct 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::moneypunct
- xlocmon/std::moneypunct::char_type
- xlocmon/std::moneypunct::string_type
- xlocmon/std::moneypunct::curr_symbol
- xlocmon/std::moneypunct::decimal_point
- xlocmon/std::moneypunct::do_curr_symbol
- xlocmon/std::moneypunct::do_decimal_point
- xlocmon/std::moneypunct::do_frac_digits
- xlocmon/std::moneypunct::do_grouping
- xlocmon/std::moneypunct::do_neg_format
- xlocmon/std::moneypunct::do_negative_sign
- xlocmon/std::moneypunct::do_pos_format
- xlocmon/std::moneypunct::do_positive_sign
- xlocmon/std::moneypunct::do_thousands_sep
- xlocmon/std::moneypunct::frac_digits
- xlocmon/std::moneypunct::grouping
- xlocmon/std::moneypunct::neg_format
- xlocmon/std::moneypunct::negative_sign
- xlocmon/std::moneypunct::pos_format
- xlocmon/std::moneypunct::positive_sign
- xlocmon/std::moneypunct::thousands_sep
helpviewer_keywords:
- std::moneypunct [C++]
- std::moneypunct [C++], char_type
- std::moneypunct [C++], string_type
- std::moneypunct [C++], curr_symbol
- std::moneypunct [C++], decimal_point
- std::moneypunct [C++], do_curr_symbol
- std::moneypunct [C++], do_decimal_point
- std::moneypunct [C++], do_frac_digits
- std::moneypunct [C++], do_grouping
- std::moneypunct [C++], do_neg_format
- std::moneypunct [C++], do_negative_sign
- std::moneypunct [C++], do_pos_format
- std::moneypunct [C++], do_positive_sign
- std::moneypunct [C++], do_thousands_sep
- std::moneypunct [C++], frac_digits
- std::moneypunct [C++], grouping
- std::moneypunct [C++], neg_format
- std::moneypunct [C++], negative_sign
- std::moneypunct [C++], pos_format
- std::moneypunct [C++], positive_sign
- std::moneypunct [C++], thousands_sep
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
ms.openlocfilehash: 8efed3cea9684c61f3bcac9eadb87b8a2b55ce09
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/03/2020
ms.locfileid: "87520936"
---
# <a name="moneypunct-class"></a>moneypunct 類別

類別樣板描述可以做為地區設定 facet 的物件，以描述用來表示貨幣輸入欄位或貨幣輸出欄位之*CharType*類型的序列。 如果範本參數*國際*為*true*，則會觀察到國際慣例。

## <a name="syntax"></a>語法

```cpp
template <class CharType, bool Intl>
class moneypunct;
```

### <a name="parameters"></a>參數

*CharType*\
用於程式內部字元編碼的類型。

*號碼*\
旗標，指定是否要遵守國際慣例。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

常數靜態物件 intl 會儲存範本參數 *Intl* 的值。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[moneypunct](#moneypunct)|`moneypunct` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[string_type](#string_type)|類型，描述包含 `CharType` 類型字元的字串。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[curr_symbol](#curr_symbol)|傳回地區設定特定的項目序列，做為貨幣符號。|
|[decimal_point](#decimal_point)|傳回地區設定特定的項目序列，做為小數點符號。|
|[do_curr_symbol](#do_curr_symbol)|受保護的虛擬成員函式，傳回地區設定特定的項目序列以做為貨幣符號。|
|[do_decimal_point](#do_decimal_point)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為小數點符號。|
|[do_frac_digits](#do_frac_digits)|受保護的虛擬成員函式傳回地區設定特定的小數點右邊位數。|
|[do_grouping](#do_grouping)|受保護的虛擬成員函式傳回決定如何將數字群組在小數點左側的地區設定特定規則。|
|[do_neg_format](#do_neg_format)|受保護的虛擬成員函式，呼叫以傳回具有負數數量的格式化輸出的地區設定特定規則。|
|[do_negative_sign](#do_negative_sign)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為負號。|
|[do_pos_format](#do_pos_format)|受保護的虛擬成員函式，呼叫以傳回具有正數數量的格式化輸出的地區設定特定規則。|
|[do_positive_sign](#do_positive_sign)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為正號。|
|[do_thousands_sep](#do_thousands_sep)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為千位分隔符號。|
|[frac_digits](#frac_digits)|傳回地區設定特定的小數點右邊位數。|
|[群組](#grouping)|傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。|
|[neg_format](#neg_format)|傳回具有負數數量的格式化輸出的地區設定特定規則。|
|[negative_sign](#negative_sign)|傳回地區設定特定的項目序列，做為負號。|
|[pos_format](#pos_format)|傳回具有正數數量的格式化輸出的地區設定特定規則。|
|[positive_sign](#positive_sign)|傳回地區設定特定的項目序列，做為正號。|
|[thousands_sep](#thousands_sep)|傳回地區設定特定的項目序列，做為千位分隔符號。|

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="moneypunctchar_type"></a><a name="char_type"></a>moneypunct：： char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 **CharType** 的同義字。

## <a name="moneypunctcurr_symbol"></a><a name="curr_symbol"></a>moneypunct：： curr_symbol

傳回地區設定特定的項目序列，做為貨幣符號。

```cpp
string_type curr_symbol() const;
```

### <a name="return-value"></a>傳回值

包含貨幣符號的字串。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_curr_symbol](#do_curr_symbol)。

### <a name="example"></a>範例

```cpp
// moneypunct_curr_symbol.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct < char, true > &mpunct = use_facet < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international currency symbol "<<  mpunct.curr_symbol( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic currency symbol "<<  mpunct2.curr_symbol( ) << endl;
};
```

## <a name="moneypunctdecimal_point"></a><a name="decimal_point"></a>moneypunct：:d ecimal_point

傳回地區設定特定的項目序列，做為小數點符號。

```cpp
CharType decimal_point() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為小數點符號。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_decimal_point](#do_decimal_point)。

### <a name="example"></a>範例

```cpp
// moneypunct_decimal_pt.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc("german_germany");

   const moneypunct < char, true > &mpunct = use_facet
      < moneypunct < char, true > >(loc);
   cout << loc.name( ) << " international decimal point "
        << mpunct.decimal_point( ) << endl;

   const moneypunct < char, false> &mpunct2 = use_facet
      < moneypunct < char, false> >(loc);
   cout << loc.name( ) << " domestic decimal point "
        << mpunct2.decimal_point( ) << endl;
}
```

```Output
German_Germany.1252 international decimal point ,
German_Germany.1252 domestic decimal point ,
```

## <a name="moneypunctdo_curr_symbol"></a><a name="do_curr_symbol"></a>moneypunct：:d o_curr_symbol

受保護的虛擬成員函式，傳回地區設定特定的項目序列以做為貨幣符號。

```cpp
virtual string_type do_curr_symbol() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為小數點符號。

### <a name="example"></a>範例

請參閱 [curr_symbol](#curr_symbol) 的範例，其中會由 `curr_symbol` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_decimal_point"></a><a name="do_decimal_point"></a>moneypunct：:d o_decimal_point

受保護的虛擬成員函式，會傳回地區設定特定的元素序列以作為貨幣符號。

```cpp
virtual CharType do_decimal_point() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為小數點符號。

### <a name="example"></a>範例

請參閱 [decimal_point](#decimal_point) 的範例，其中會由 `decimal_point` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_frac_digits"></a><a name="do_frac_digits"></a>moneypunct：:d o_frac_digits

受保護的虛擬成員函式，會傳回地區設定特定的小數點右邊位數。

```cpp
virtual int do_frac_digits() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的小數點右邊位數。

### <a name="example"></a>範例

請參閱 [frac_digits](#frac_digits) 的範例，其中會由 `frac_digits` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_grouping"></a><a name="do_grouping"></a>moneypunct：:d o_grouping

受保護的虛擬成員函式，會傳回地區設定特定規則，來決定任何小數點左邊數字分組的方式。

```cpp
virtual string do_grouping() const;
```

### <a name="return-value"></a>傳回值

地區設定特定規則，用來決定任何小數點左邊數字分組的方式。

### <a name="example"></a>範例

請參閱[群組](#grouping)的範例，其中會呼叫虛擬成員函式 `grouping` 。

## <a name="moneypunctdo_neg_format"></a><a name="do_neg_format"></a>moneypunct：:d o_neg_format

受保護的虛擬成員函式，呼叫以傳回具有負數數量的格式化輸出的地區設定特定規則。

```cpp
virtual pattern do_neg_format() const;
```

### <a name="return-value"></a>傳回值

受保護的虛擬成員函式會傳回地區設定特定規則，來決定如何為負數金額產生貨幣輸出欄位。 四個元素中的每個都 `pattern::field` 可以有下列值：

- `none`符合零或多個空格，或不產生任何內容。

- `sign`若要比對或產生正號或負號。

- `space`表示比對零個或多個空格或產生空格。

- `symbol`符合或產生貨幣符號。

- `value`以符合或產生貨幣值。

會產生貨幣輸出欄位的元件，而貨幣輸入欄位的元件會依照這些元素出現的順序進行比對 `pattern::field` 。 每個值 `sign` 、 `symbol` 、和都 `value` `none` `space` 必須只出現一次。 此值 `none` 不能先出現。 此值 `space` 不得出現在 first 或 last。 如果 `Intl` 為 true，則順序為 `symbol` 、 `sign` 、 `none` 、then `value` 。

的範本版本會 `moneypunct< CharType, Intl >` 傳回 `{money_base::symbol, money_base::sign, money_base::value, money_base::none}` 。

### <a name="example"></a>範例

請參閱 [neg_format](#neg_format) 的範例，其中會由 `neg_format` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_negative_sign"></a><a name="do_negative_sign"></a>moneypunct：:d o_negative_sign

受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為負號。

```cpp
virtual string_type do_negative_sign() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為負號。

### <a name="example"></a>範例

請參閱 [negative_sign](#negative_sign) 的範例，其中會由 `negative_sign` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_pos_format"></a><a name="do_pos_format"></a>moneypunct：:d o_pos_format

受保護的虛擬成員函式，呼叫以傳回具有正數數量的格式化輸出的地區設定特定規則。

```cpp
virtual pattern do_pos_format() const;
```

### <a name="return-value"></a>傳回值

受保護的虛擬成員函式會傳回地區設定特定規則，來決定如何為正數金額產生貨幣輸出欄位。 （它也會決定如何比對貨幣輸入欄位的元件）。編碼方式與[do_neg_format](#do_neg_format)相同。

的範本版本會 `moneypunct< CharType, Inputlterator >` 傳回 `{ money_base::symbol, money_base::sign, money_base::value, money_base::none }` 。

### <a name="example"></a>範例

請參閱 [pos_format](#pos_format) 的範例，其中會由 `pos_format` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_positive_sign"></a><a name="do_positive_sign"></a>moneypunct：:d o_positive_sign

受保護的虛擬成員函式，會傳回地區設定特定的元素序列以作為正號。

```cpp
virtual string_type do_positive_sign() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為正號。

### <a name="example"></a>範例

請參閱 [positive_sign](#positive_sign) 的範例，其中會由 `positive_sign` 呼叫此虛擬成員函式。

## <a name="moneypunctdo_thousands_sep"></a><a name="do_thousands_sep"></a>moneypunct：:d o_thousands_sep

受保護的虛擬成員函式，會傳回地區設定特定的元素，用來作為任何小數點左邊的群組分隔符號。

```cpp
virtual CharType do_thousands_sep() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素，用來作為任何小數點左邊的群組分隔符號。

### <a name="example"></a>範例

請參閱 [thousands_sep](#thousands_sep) 的範例，其中會由 `thousands_sep` 呼叫此虛擬成員函式。

## <a name="moneypunctfrac_digits"></a><a name="frac_digits"></a>moneypunct：： frac_digits

傳回地區設定特定的小數點右邊位數。

```cpp
int frac_digits() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的小數點右邊位數。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_frac_digits](#do_frac_digits)。

### <a name="example"></a>範例

```cpp
// moneypunct_frac_digits.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >(loc);
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >(loc);
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctgrouping"></a><a name="grouping"></a>moneypunct：：群組

傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。

```cpp
string grouping() const;
```

### <a name="return-value"></a>傳回值

地區設定特定規則，用來決定任何小數點左邊數字分組的方式。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_grouping](#do_grouping)。

### <a name="example"></a>範例

```cpp
// moneypunct_grouping.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true> >( loc );
   for (unsigned int i = 0; i <mpunct.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " international grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " international frac_digits\n to the right"
        << " of the radix character: "
        << mpunct.frac_digits ( ) << endl << endl;

   const moneypunct <char, false> &mpunct2 =
       use_facet <moneypunct <char, false> >( loc );
   for (unsigned int i = 0; i <mpunct2.grouping( ).length( ); i++ )
   {
      cout << loc.name( ) << " domestic grouping:\n the "
           << i <<"th group to the left of the radix character "
           << "is of size " << (int)(mpunct2.grouping ( )[i])
           << endl;
   }
   cout << loc.name( ) << " domestic frac_digits\n to the right"
        << " of the radix character: "
        << mpunct2.frac_digits ( ) << endl << endl;
}
```

```Output
German_Germany.1252 international grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 international frac_digits
to the right of the radix character: 2

German_Germany.1252 domestic grouping:
the 0th group to the left of the radix character is of size 3
German_Germany.1252 domestic frac_digits
to the right of the radix character: 2
```

## <a name="moneypunctmoneypunct"></a><a name="moneypunct"></a>moneypunct：： moneypunct

`moneypunct` 類型物件的建構函式。

```cpp
explicit moneypunct(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*_Refs*參數和其重要性的可能值為：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1：未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式會以 [locale::facet](../standard-library/locale-class.md#facet_class)(_ *Refs*) 將其基底物件初始化。

## <a name="moneypunctneg_format"></a><a name="neg_format"></a>moneypunct：： neg_format

傳回具有負數數量的格式化輸出的地區設定特定規則。

```cpp
pattern neg_format() const;
```

### <a name="return-value"></a>傳回值

地區設定特定規則，用來將具有負數金額的輸出格式化。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_neg_format](#do_neg_format)。

### <a name="example"></a>範例

```cpp
// moneypunct_neg_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( ) {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international negative number format: "
        << mpunct.neg_format( ).field[0]
        << mpunct.neg_format( ).field[1]
        << mpunct.neg_format( ).field[2]
        << mpunct.neg_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative number format: "
        << mpunct2.neg_format( ).field[0]
        << mpunct2.neg_format( ).field[1]
        << mpunct2.neg_format( ).field[2]
        << mpunct2.neg_format( ).field[3] << endl;
}
```

## <a name="moneypunctnegative_sign"></a><a name="negative_sign"></a>moneypunct：： negative_sign

傳回地區設定特定的項目序列，做為負號。

```cpp
string_type negative_sign() const;
```

### <a name="return-value"></a>傳回值

傳回地區設定特定的項目序列，做為負號。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_negative_sign](#do_negative_sign)。

### <a name="example"></a>範例

```cpp
// moneypunct_neg_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international negative sign: "
        << mpunct.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic negative sign: "
        << mpunct2.negative_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international negative sign: "
        << mpunct3.negative_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic negative sign: "
        << mpunct4.negative_sign( ) << endl;
};
```

```Output
German_Germany.1252 international negative sign: -
German_Germany.1252 domestic negative sign: -
French_France.1252 international negative sign: -
French_France.1252 domestic negative sign: -
```

## <a name="moneypunctpos_format"></a><a name="pos_format"></a>moneypunct：:p os_format

傳回具有正數數量的格式化輸出的地區設定特定規則。

```cpp
pattern pos_format() const;
```

### <a name="return-value"></a>傳回值

地區設定特定規則，用來將具有正數金額的輸出格式化。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_pos_format](#do_pos_format)。

### <a name="example"></a>範例

```cpp
// moneypunct_pos_format.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main() {
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true> >(loc);
   cout << loc.name( ) << " international positive number format: "
        << mpunct.pos_format( ).field[0]
        << mpunct.pos_format( ).field[1]
        << mpunct.pos_format( ).field[2]
        << mpunct.pos_format( ).field[3] << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive number format: "
        << mpunct2.pos_format( ).field[0]
        << mpunct2.pos_format( ).field[1]
        << mpunct2.pos_format( ).field[2]
        << mpunct2.pos_format( ).field[3] << endl;
}
```

## <a name="moneypunctpositive_sign"></a><a name="positive_sign"></a>moneypunct：:p ositive_sign

傳回地區設定特定的項目序列，做為正號。

```cpp
string_type positive_sign() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為正號。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_positive_sign](#do_positive_sign)。

### <a name="example"></a>範例

```cpp
// moneypunct_pos_sign.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>

using namespace std;

int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
      use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international positive sign:"
        << mpunct.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic positive sign:"
        << mpunct2.positive_sign( ) << endl;

   locale loc2( "French" );

   const moneypunct <char, true> &mpunct3 =
      use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international positive sign:"
        << mpunct3.positive_sign( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic positive sign:"
        << mpunct4.positive_sign( ) << endl;
};
```

```Output
German_Germany.1252 international positive sign:
German_Germany.1252 domestic positive sign:
French_France.1252 international positive sign:
French_France.1252 domestic positive sign:
```

## <a name="moneypunctstring_type"></a><a name="string_type"></a>moneypunct：： string_type

類型，描述包含 **CharType** 類型字元的字串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>備註

此類型描述類別樣板的特製化， [basic_string](../standard-library/basic-string-class.md)其物件可以儲存標點符號序列的複本。

## <a name="moneypunctthousands_sep"></a><a name="thousands_sep"></a>moneypunct：： thousands_sep

傳回地區設定特定的項目序列，做為千位分隔符號。

```cpp
CharType thousands_sep() const;
```

### <a name="return-value"></a>傳回值

地區設定特定的元素序列，用來作為千分號。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_thousands_sep](#do_thousands_sep)。

### <a name="example"></a>範例

```cpp
// moneypunct_thou_sep.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   const moneypunct <char, true> &mpunct =
       use_facet <moneypunct <char, true > >(loc);
   cout << loc.name( ) << " international thousands separator: "
        << mpunct.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct2 =
      use_facet <moneypunct <char, false> >(loc);
   cout << loc.name( ) << " domestic thousands separator: "
        << mpunct2.thousands_sep( ) << endl << endl;

   locale loc2( "english_canada" );

   const moneypunct <char, true> &mpunct3 =
       use_facet <moneypunct <char, true> >(loc2);
   cout << loc2.name( ) << " international thousands separator: "
        << mpunct3.thousands_sep( ) << endl;

   const moneypunct <char, false> &mpunct4 =
      use_facet <moneypunct <char, false> >(loc2);
   cout << loc2.name( ) << " domestic thousands separator: "
        << mpunct4.thousands_sep( ) << endl;
}
```

```Output
German_Germany.1252 international thousands separator: .
German_Germany.1252 domestic thousands separator: .

English_Canada.1252 international thousands separator: ,
English_Canada.1252 domestic thousands separator: ,
```

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
