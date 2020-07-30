---
title: num_put 類別
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_put
- locale/std::num_put::char_type
- locale/std::num_put::iter_type
- locale/std::num_put::do_put
- locale/std::num_put::put
helpviewer_keywords:
- std::num_put [C++]
- std::num_put [C++], char_type
- std::num_put [C++], iter_type
- std::num_put [C++], do_put
- std::num_put [C++], put
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
ms.openlocfilehash: 32bfc29b7bc645dd37ae4aaaf498823c0d139dfc
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224704"
---
# <a name="num_put-class"></a>num_put 類別

類別樣板，描述可以做為地區設定 facet 的物件，以控制數值轉換為類型的序列 `CharType` 。

## <a name="syntax"></a>語法

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>參數

*CharType*\
程式內用於編碼地區設定字元的類型。

*OutputIterator*\
數值 put 函式將其輸出寫入其中的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[num_put](#num_put)|`num_put` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸出迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_put](#do_put)|虛擬函式，呼叫以將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|
|[提出](#put)|將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put：： char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put：:d o_put

虛擬函式，呼叫以將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。

```cpp
virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const unsigned long long val) const;
```

### <a name="parameters"></a>參數

*下一個*\
迭代器，定址對象是所插入字串的第一個元素。

*_Iosbase*\
指定的資料流，其中包含帶有 numpunct facet 的地區設定，可用來為輸出和旗標加上標點符號以設定輸出格式。

*_Fill*\
間距所使用的字元。

*初始值*\
要輸出的數字或布林值類型。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。

### <a name="remarks"></a>備註

第一個虛擬的受保護成員函式會產生從*下一個*開始的順序元素，以從*val*的值產生整數輸出欄位。 此函式會傳回迭代器，此迭代器指定在所產生的整數輸出欄位後下一個要插入元素的位置。

整數輸出欄位是由列印函式用來產生一系列元素至檔案的相同規則所產生 **`char`** 。 每個這類 char 元素都假設為對應至類型的對等專案 `CharType` ，方法是使用簡單的一對一對應。 不過，當 print 函式將含有空格或數位0的欄位填補時，會 `do_put` 改為使用 `fill` 。 對等的列印轉換規格是以下列方式決定：

- 如果 **iosbase**. [旗](../standard-library/ios-base-class.md#flags)  &  `ios_base::basefield` 標  ==  `ios_base::`[oct](../standard-library/ios-functions.md#oct)，轉換規格為 `lo` 。

- 如果**iosbase**為  &  **ios_base：： basefield**  ==  `ios_base::` [hex](../standard-library/ios-functions.md#hex)，則轉換規格為 `lx` 。

- 否則，轉換規格會是 `ld`。

如果 **iosbase**. [width](../standard-library/ios-base-class.md#width) 不是零，就會在前面加上此值的欄位寬度。 接著，函式會呼叫 **iosbase**. **width**(0) 將欄位寬度重設為零。

只有當指定輸出欄位所需的元素數目下限 *N* 小於 **iosbase**. [width](../standard-library/ios-base-class.md#width)。 這類填補包含 [填滿] 的*N*個  -  **寬度**複本順序**fill**。 接著，填補會以下列方式進行：

- 如果 **iosbase**. **旗**  &  `ios_base::adjustfield` 標  ==  `ios_base::`[left](../standard-library/ios-functions.md#left)，會在前面加上旗標 **-** 。 (填補的發生位置是在已產生的文字之後)。

- 如果**iosbase**  &  **：： adjustfield**  ==  `ios_base::` [internal](../standard-library/ios-functions.md#internal)ios_base，則會在前面加上旗標**0** 。 (就數字輸出欄位而言，會在列印函式以 0 填補的地方進行填補)。

- 否則，不會在前面加上任何額外的旗標。 (填補字元會出現在已產生的序列之前)。

最後：

- 如果 **iosbase**. **旗標**  &  `ios_base::`[showpos](../standard-library/ios-functions.md#showpos)為非零值，此旗標會加在 **+** 轉換規格的前面。

- 如果 **iosbase**. **旗標**  & **ios_base：：**[showbase](../standard-library/ios-functions.md#showbase)不是零，此旗標會加在 **#** 轉換規格的前面。

整數輸出欄位的格式會進一步由呼叫[use_facet](../standard-library/locale-functions.md#use_facet) [locale facet](../standard-library/locale-class.md#facet_class) **fac**  <  [numpunct](../standard-library/numpunct-class.md) \< **Elem**> （ **iosbase**）所傳回的地區設定 facet fac 決定。 [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。 明確說來：

- **fac**. [群組](../standard-library/numpunct-class.md#grouping)決定如何將數位群組在任何小數點左邊

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep)決定分隔小數點左邊數位群組的順序

如果 **fac**. **grouping** (其第一個元素的值為 CHAR_MAX) 未施加任何千分號條件約束，就不會有任何 **fac**. `thousands_sep` 執行個體在輸出欄位中產生。 否則，會在進行列印轉換之後插入分隔符號。

第二個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    unsigned long val) const;
```

行為與第一個相同，不同的是，它會以 `lu` 取代 `ld` 轉換規格。

第三個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    double val) const;
```

行為與第一個相同，不同的是，它會從 **val** 的值產生浮點數輸出欄位。 **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) 會決定將整數與小數分隔的序列。 對等的列印轉換規格是以下列方式決定：

- 如果 **iosbase**. **旗**  &  `ios_base::floatfield` 標  ==  `ios_base::`已[修正](../standard-library/ios-functions.md#fixed)，轉換規格為 `lf` 。

- 如果 **iosbase**. **旗標**  & **ios_base：： floatfield**  ==  `ios_base::`[科學](../standard-library/ios-functions.md#scientific)，轉換規格為 `le` 。 如果 **iosbase**. **旗標**  &  `ios_base::`[大寫](../standard-library/ios-functions.md#uppercase)為非零值， `e` 取代為 `E` 。

- 否則，轉換規格會是 **lg**。 如果 **iosbase**. **旗標**  & **ios_base：：大寫**不是零， `g` 已取代為 `G` 。

如果 **iosbase**. **旗標**  & **ios_base：： fixed**為非零值，如果**iosbase**，則為。 [precision](../standard-library/ios-base-class.md#precision) 大於零，就會在轉換規格前面加上值為 **iosbase**. **precision** 的有效位數。 所有填補行為都與整數輸出欄位的填補行為相同。 填補字元為 **fill**。 最後：

- 如果 **iosbase**. **旗標**  &  `ios_base::`[showpos](../standard-library/ios-functions.md#showpos)為非零值，此旗標會加在 **+** 轉換規格的前面。

- 如果 **iosbase**. **旗標**  &  `ios_base::`[showpoint](../standard-library/ios-functions.md#showpoint)為非零值，此旗標會加在 **#** 轉換規格的前面。

第四個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

的行為與第三個相同，不同之處在于 `l` 轉換規格中的限定詞會取代為 `L` 。

第五個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    const void* val) const;
```

行為與第一個相同，不同的是，轉換規格為 `p`**,** 再加上指定填補時所需的任何限定詞。

第六個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    bool val) const;
```

行為與第一個相同，不同之處在于它會從*val*產生布林輸出欄位。

布林值輸出欄位採用下列兩種形式其中之一。 如果 `iosbase.flags & ios_base::` [boolAlpha](../standard-library/ios-functions.md#boolalpha)為 **`false`** ，則成員函式會傳回 `do_put(_Next, _Iosbase, _Fill, (long)val)` ，這通常會產生0（適用于 **`false`** ）或1（適用于）的產生序列 **`true`** 。 否則，產生的序列可能是*fac*。[falsename](../standard-library/numpunct-class.md#falsename) （適用于 **`false`** ），或*fac*。[truename](../standard-library/numpunct-class.md#truename) （適用于 **`true`** ）。

第七個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    long long val) const;
```

行為與第一個相同，不同的是，它會以 `lld` 取代 `ld` 轉換規格。

第八個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,
    Elem fill,
    unsigned long long val) const;
```

行為與第一個相同，不同的是，它會以 `llu` 取代 `ld` 轉換規格。

### <a name="example"></a>範例

請參閱 [put](#put) 的範例，其會呼叫 `do_put`。

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put：： iter_type

描述輸出迭代器的類型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型與範本參數**OutputIterator 同義。**

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put：： num_put

`num_put` 類型物件的建構函式。

```cpp
explicit num_put(size_t _Refs = 0);
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

此函式會使用**locale：：**[Facet](../standard-library/locale-class.md#facet_class)（_ *Refs*）將其基底物件初始化。

## <a name="num_putput"></a><a name="put"></a>num_put：:p 的

將數位轉換成序列 `CharType` ，表示為指定地區設定格式化的數位。

```cpp
iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    bool val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    unsigned long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    Unsigned long long val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    long double val) const;

iter_type put(
    iter_type dest,
    ios_base& _Iosbase,
    _Elem _Fill,
    const void* val) const;
```

### <a name="parameters"></a>參數

*dest*\
迭代器，定址對象是所插入字串的第一個元素。

*_Iosbase*\
指定的資料流，其中包含帶有 numpunct facet 的地區設定，可用來為輸出和旗標加上標點符號以設定輸出格式。

*_Fill*\
間距所使用的字元。

*初始值*\
要輸出的數字或布林值類型。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。

### <a name="remarks"></a>備註

所有成員函式都會傳回[do_put](#do_put)（ `next` 、 `_Iosbase` 、 `_Fill` 、 `val` ）。

### <a name="example"></a>範例

```cpp
// num_put_put.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );
   basic_stringstream<char> psz2;
   ios_base::iostate st = 0;
   long double fVal;
   cout << "The thousands separator is: "
        << use_facet < numpunct <char> >(loc).thousands_sep( )
        << endl;

   psz2.imbue( loc );
   use_facet < num_put < char > >
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),
                    psz2, ' ', fVal=1000.67);

   if ( st & ios_base::failbit )
      cout << "num_put( ) FAILED" << endl;
   else
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;
}
```

```Output
The thousands separator is: .
num_put( ) = 1.000,67
```

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)\
[facet 類別](../standard-library/locale-class.md#facet_class)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
