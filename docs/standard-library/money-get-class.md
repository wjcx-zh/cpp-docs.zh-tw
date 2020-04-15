---
title: money_get 類別
ms.date: 11/04/2016
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
ms.openlocfilehash: ac85e99bfb834fd970a804269f25ec9f20960a23
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375907"
---
# <a name="money_get-class"></a>money_get 類別

類範本描述一個物件,該物件可用作區域設置,用於控制類型`CharType`序列轉換為貨幣值。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>參數

*字元類型*\
程式內用於編碼地區設定字元的類型。

*輸入反覆運算器*\
get 函式從中讀取其輸入的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[money_get](#money_get)|`money_get` 類型物件的建構函式，用來從表示貨幣值的序列擷取數值。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸入迭代器的類型。|
|[string_type](#string_type)|類型，描述包含 `CharType` 類型字元的字串。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_get](#do_get)|虛擬函式，呼叫以從代表貨幣值的字元序列擷取數值。|
|[get](#get)|從代表貨幣值的字元序列擷取數值。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="money_getchar_type"></a><a name="char_type"></a>money_get:char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 *CharType* 的同義字。

## <a name="money_getdo_get"></a><a name="do_get"></a>money_get::d

虛擬函式，呼叫此函式可從代表貨幣值的字元序列中擷取數值。

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*國際*\
布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*瓦爾*\
儲存已轉換之序列的字串。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是貨幣輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

第一個虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的貨幣輸入欄位為止。 如果成功,它將此欄位轉換為一個或多個十進位數字序列,選項前面有一個減號 (),`-`以表示金額並將結果存儲在[string_type](#string_type)物件*val*中。 它會傳回迭代器，此迭代器指定貨幣輸入欄位後的第一個元素。 否則,函數將空序列存儲在*val*`ios_base::failbit`中, 並在*狀態*中設置。 它會傳回迭代器，此迭代器指定有效貨幣輸入欄位之任何前置詞後的第一個元素。 不論是上述哪一種情況，如果傳回值等於 `last`，函式就會在 `State` 中設定 `ios_base::eofbit`。

第二個虛擬受保護成員函數的表示行為與第一個函數相同,但成功時,它將可選簽名的數位序列轉換為**長雙**型值,並將該值存儲在*val*。

貨幣輸入欄位的格式會由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。

具體來說：

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 會決定欄位的元素出現順序。

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 會決定構成貨幣符號的元素序列。

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 會決定構成正號的元素序列。

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 會決定構成負號的元素序列。

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 會決定任何小數點左邊數字分組的方式。

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 會決定任何小數點左邊分隔數字群組的元素。

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 會決定將整數與小數分隔的元素。

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 會決定任何小數點右邊的有效小數數目。 剖析貨幣金額時，如果小數位數多於 `frac_digits` 所需的小數位數，`do_get` 在取用最多 `frac_digits` 個字元後就會停止剖析。

如果正負號字串 ( **fac**. `negative_sign` 或 **fac**. `positive_sign`) 有多個元素，將只會在格式模式中與 **money_base::sign** 相等之元素出現的位置，比對第一個元素，其中該格式模式為 ( **fac**. `neg_format`). 所有其餘元素則是在貨幣輸入欄位結尾進行比對。 如果兩個字串都沒有與貨幣輸入欄位中下一個元素相符的第一個元素，正負號字串就會被視為空的而採用正號。

如果 **iosbase**. [標誌](../standard-library/ios-base-class.md#flags) & [顯示函式](../standard-library/ios-functions.md#showbase)庫是非零的,字串**fac**。 `curr_symbol` 就必須在格式模式中與 **money_base::symbol** 相等之元素出現的位置進行比對。 否則，如果 **money_base::symbol** 出現在格式模式結尾，又如果沒有任何其餘正負號字串元素可供比對，就不會比對貨幣符號。 否則，會視需要比對貨幣符號。

如果沒有任何 **fac**. `thousands_sep` 執行個體出現在貨幣輸入欄位的值部分 (格式模式中與 **money_base::value** 相等之元素出現的位置)，就不會施加任何千分號條件約束。 否則，將會強制執行 **fac**. **grouping** 所施加的任何千分號條件約束。 請注意，產生的數字序列代表一個整數，其低序位 **fac**. `frac_digits` 十進位數字被視為在小數點右邊。

在格式模式中與 **money_base::space** 相等之元素出現的位置，只要該元素不是出現在格式模式結尾，就會進行任意空白字元比對。 否則，不會比對任何內部空白字元。 *ch* 元素會被視為空白字元，如果 [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。 [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) 為 **true** 的話。

### <a name="example"></a>範例

請參閱 [get](#get) 的範例，它會呼叫 `do_get`。

## <a name="money_getget"></a><a name="get"></a>money_get:取得

從代表貨幣值的字元序列擷取數值。

```cpp
iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool Intl,
    ios_base& Iosbase,
    ios_base::iostate& State,
    string_type& val) const;
```

### <a name="parameters"></a>參數

*第一*\
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後*\
輸入迭代器，定址對象是要轉換之序列的結尾。

*國際*\
布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。

*約斯基地*\
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*\
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*瓦爾*\
儲存已轉換之序列的字串。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是貨幣輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

兩個成員函數都傳回[do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`。

### <a name="example"></a>範例

```cpp
// money_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;

int main( )
{
   locale loc( "german_germany" );

   basic_stringstream< char > psz;
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";
   basic_stringstream< char > psz2;
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();

   ios_base::iostate st = 0;
   long double fVal;

   psz.flags( psz.flags( )|ios_base::showbase );
   // Which forced the READING the currency symbol
   psz.imbue(loc);
   use_facet < money_get < char > >( loc ).
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"
           << endl;
   else
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "
           << fVal/100.0 << endl;

   use_facet < money_get < char > >( loc ).
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);

   if ( st & ios_base::failbit )
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"
           << endl;
   else
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "
           << fVal/100.0 << endl;
};
```

## <a name="money_getiter_type"></a><a name="iter_type"></a>money_get:iter_type

描述輸入迭代器的類型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 **InputIterator** 同義。

## <a name="money_getmoney_get"></a><a name="money_get"></a>money_get:money_get

`money_get` 類型物件的建構函式，用來從表示貨幣值的序列擷取數值。

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*_Refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1: 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函數用區域設置初始化其基本物件 **::**[分](../standard-library/locale-class.md#facet_class)*面(_Refs*)。

## <a name="money_getstring_type"></a><a name="string_type"></a>money_get:string_type

類型，描述包含 **CharType** 類型字元的字串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>備註

該類型描述了類範本的專門化[basic_string。](../standard-library/basic-string-class.md)

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[分面類](../standard-library/locale-class.md#facet_class)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
