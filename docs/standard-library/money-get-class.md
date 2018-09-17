---
title: money_get 類別 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- xlocmon/std::money_get
- xlocmon/std::money_get::char_type
- xlocmon/std::money_get::iter_type
- xlocmon/std::money_get::string_type
- xlocmon/std::money_get::do_get
- xlocmon/std::money_get::get
dev_langs:
- C++
helpviewer_keywords:
- std::money_get [C++]
- std::money_get [C++], char_type
- std::money_get [C++], iter_type
- std::money_get [C++], string_type
- std::money_get [C++], do_get
- std::money_get [C++], get
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 991c8c9505485e84aa4e8e1e0e8955b5ad2ac23a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45712845"
---
# <a name="moneyget-class"></a>money_get 類別

此樣板類別描述可以做為地區設定 facet 的物件，以控制類型 `CharType` 的序列轉換為貨幣值。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class money_get : public locale::facet;
```

### <a name="parameters"></a>參數

*CharType*<br/>
程式內用於編碼地區設定字元的類型。

*InputIterator*<br/>
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

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[do_get](#do_get)|虛擬函式，呼叫以從代表貨幣值的字元序列擷取數值。|
|[get](#get)|從代表貨幣值的字元序列擷取數值。|

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="char_type"></a>  money_get::char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數 *CharType* 同義。

## <a name="do_get"></a>  money_get::do_get

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

*first*<br/>
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後一個*<br/>
輸入迭代器，定址對象是要轉換之序列的結尾。

*Intl*<br/>
布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。

*iosbase*<br/>
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*<br/>
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*val*<br/>
儲存已轉換之序列的字串。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是貨幣輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

第一個虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的貨幣輸入欄位為止。 如果成功，它將此欄位轉換為一連串的一或多個十進位數字可以選擇性加上負號 ( `-`)，以代表承諾用量金額，並將結果[string_type](#string_type)物件*val*. 它會傳回迭代器，此迭代器指定貨幣輸入欄位後的第一個元素。 否則，函式會儲存在空的序列*val*並設定`ios_base::failbit`中*狀態*。 它會傳回迭代器，此迭代器指定有效貨幣輸入欄位之任何前置詞後的第一個元素。 不論是上述哪一種情況，如果傳回值等於 `last`，函式就會在 `State` 中設定 `ios_base::eofbit`。

第二個受保護的虛擬成員函式行為與第一個相同，不同之處在於如果成功的話就選擇性帶正負號的數字將序列轉換成類型的值**長雙精度**並將該值儲存在*val*.

貨幣輸入欄位的格式會由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**>>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 有效呼叫所傳回) 決定。

尤其是：

- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 會決定欄位的元素出現順序。

- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 會決定構成貨幣符號的元素序列。

- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 會決定構成正號的元素序列。

- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 會決定構成負號的元素序列。

- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 會決定任何小數點左邊數字分組的方式。

- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 會決定任何小數點左邊分隔數字群組的元素。

- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 會決定將整數與小數分隔的元素。

- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 會決定任何小數點右邊的有效小數數目。 剖析貨幣金額時，如果小數位數多於 `frac_digits` 所需的小數位數，`do_get` 在取用最多 `frac_digits` 個字元後就會停止剖析。

如果正負號字串 ( **fac**. `negative_sign` 或 **fac**. `positive_sign`) 有多個元素，將只會在格式模式中與 **money_base::sign** 相等之元素出現的位置，比對第一個元素，其中該格式模式為 ( **fac**. `neg_format`)。 所有其餘元素則是在貨幣輸入欄位結尾進行比對。 如果兩個字串都沒有與貨幣輸入欄位中下一個元素相符的第一個元素，正負號字串就會被視為空的而採用正號。

如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) 不為零，字串 **fac**. `curr_symbol` 就必須在格式模式中與 **money_base::symbol** 相等之元素出現的位置進行比對。 否則，如果 **money_base::symbol** 出現在格式模式結尾，又如果沒有任何其餘正負號字串元素可供比對，就不會比對貨幣符號。 否則，會視需要比對貨幣符號。

如果沒有任何 **fac**. `thousands_sep` 執行個體出現在貨幣輸入欄位的值部分 (格式模式中與 **money_base::value** 相等之元素出現的位置)，就不會施加任何千分號條件約束。 否則，將會強制執行 **fac**. **grouping** 所施加的任何千分號條件約束。 請注意，產生的數字序列代表一個整數，其低序位 **fac**. `frac_digits` 十進位數字被視為在小數點右邊。

在格式模式中與 **money_base::space** 相等之元素出現的位置，只要該元素不是出現在格式模式結尾，就會進行任意空白字元比對。 否則，不會比對任何內部空白字元。 *ch* 元素會被視為空白字元，如果 [use_facet](../standard-library/locale-functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)). [is](../standard-library/ctype-class.md#is)( **ctype_base::space**, *ch*) 為 **true** 的話。

### <a name="example"></a>範例

請參閱 [get](#get) 的範例，它會呼叫 `do_get`。

## <a name="get"></a>  money_get::get

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

*first*<br/>
輸入迭代器，定址對象是要轉換之序列的開頭。

*最後一個*<br/>
輸入迭代器，定址對象是要轉換之序列的結尾。

*Intl*<br/>
布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。

*iosbase*<br/>
格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。

*狀態*<br/>
根據作業是否成功，為資料流狀態設定適當的位元遮罩元素。

*val*<br/>
儲存已轉換之序列的字串。

### <a name="return-value"></a>傳回值

輸入迭代器，定址對象是貨幣輸入欄位後的第一個元素。

### <a name="remarks"></a>備註

這兩個成員函式會傳回[do_get](#do_get)`(first, last, Intl, Iosbase, State, val)`。

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

## <a name="iter_type"></a>  money_get::iter_type

描述輸入迭代器的類型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型與範本參數 **InputIterator** 同義。

## <a name="money_get"></a>  money_get::money_get

`money_get` 類型物件的建構函式，用來從表示貨幣值的序列擷取數值。

```cpp
explicit money_get(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*<br/>
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

可能值 *_Refs*參數和其意義如下：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \> 1： 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式會初始化其基底物件**地區設定::**[facet](../standard-library/locale-class.md#facet_class)(*_Refs*)。

## <a name="string_type"></a>  money_get::string_type

一種類型，描述包含 **CharType** 類型字元的字串。

```cpp
typedef basic_string<CharType, Traits, Allocator> string_type;
```

### <a name="remarks"></a>備註

此類型描述 [basic_string](../standard-library/basic-string-class.md) 範本類別的特製化。

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)<br/>
[facet 類別](../standard-library/locale-class.md#facet_class)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
