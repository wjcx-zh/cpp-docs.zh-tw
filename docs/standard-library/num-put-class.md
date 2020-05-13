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
ms.openlocfilehash: 3f65d7140bb5c691fa58ec9d74ceda5573280ddb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373638"
---
# <a name="num_put-class"></a>num_put 類別

一個類範本,用於描述可用作區域設置面的物件,用於控制數值轉換為類型序列`CharType`的物件。

## <a name="syntax"></a>語法

```cpp
template <class CharType,
    class OutputIterator = ostreambuf_iterator<CharType>>
class num_put : public locale::facet;
```

### <a name="parameters"></a>參數

*字元類型*\
程式內用於編碼地區設定字元的類型。

*輸出反覆運算器*\
數值 put 函式將其輸出寫入其中的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[num_put](#num_put)|`num_put` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸出迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_put](#do_put)|虛擬函式，呼叫以將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|
|[把](#put)|將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="num_putchar_type"></a><a name="char_type"></a>num_put:char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

## <a name="num_putdo_put"></a><a name="do_put"></a>num_put::do_put

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

*瓦爾*\
要輸出的數字或布林值類型。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。

### <a name="remarks"></a>備註

第一個虛擬受保護成員函數生成順序元素,從*下一個*開始,從*val*生成整數輸出欄位。 此函式會傳回迭代器，此迭代器指定在所產生的整數輸出欄位後下一個要插入元素的位置。

整數輸出欄位由列印函數用於向檔生成一系列**字元**元素的相同規則生成。 假定每個此類字元元素都通過簡單的一對一映射映射到等效`CharType`類型的元素。 但是,如果列印函數使用空白或數位 0 的欄位`do_put`, 則`fill`改用 。 對等的列印轉換規格是以下列方式決定：

- 如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags)`lo`[oct](../standard-library/ios-functions.md#oct) == 標誌 十年,轉換規範是。`ios_base::`  & `ios_base::basefield`

- 如果**iosbase.flags** & **ios_base:基場** == `ios_base::`[十六進位](../standard-library/ios-functions.md#hex),則轉換`lx`規格為 。

- 否則，轉換規格會是 `ld`。

如果 **iosbase**. [width](../standard-library/ios-base-class.md#width) 不是零，就會在前面加上此值的欄位寬度。 接著，函式會呼叫 **iosbase**. **width**(0) 將欄位寬度重設為零。

只有當指定輸出欄位所需的元素數目下限 *N* 小於 **iosbase**. [寬度](../standard-library/ios-base-class.md#width)。 此類填充由**填充**的*N* - **寬度**副本序列組成。 接著，填補會以下列方式進行：

- 如果 **iosbase**. **flags** == [left](../standard-library/ios-functions.md#left)`ios_base::adjustfield`標誌向左,標誌已預告。`ios_base::`  &  **-** (填補的發生位置是在已產生的文字之後)。

- 如果**iosbase.標誌** & **ios_base:調整欄位** == `ios_base::`[內部](../standard-library/ios-functions.md#internal),則標誌**0**已預告。 (就數字輸出欄位而言，會在列印函式以 0 填補的地方進行填補)。

- 否則，不會在前面加上任何額外的旗標。 (填補字元會出現在已產生的序列之前)。

最後：

- 如果 **iosbase**. **flags**標誌 顯示波 是非零**+**,標誌 已準備到轉換規範。[showpos](../standard-library/ios-functions.md#showpos)  & `ios_base::`

- 如果 **iosbase**. **標誌** & **ios_base:顯示**[庫](../standard-library/ios-functions.md#showbase)為非**#** 零,標誌 已準備到轉換規範。

整數輸出欄位的格式會進一步由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。 具體來說：

- **fac**. [群組](../standard-library/numpunct-class.md#grouping)確定數位如何群組到任何小數點左側

- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep)確定將數位群組分隔到任何小數點左側的序列

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

- 如果 **iosbase**. **flags**`lf`[fixed](../standard-library/ios-functions.md#fixed) == 標頭固定,轉換規範為 。`ios_base::`  & `ios_base::floatfield`

- 如果 **iosbase**. **標誌** & **ios_base:浮場** == `ios_base::`[科學](../standard-library/ios-functions.md#scientific),`le`轉換規範是 。 如果 **iosbase**. **flags**`ios_base::``e``E`標頭[大寫](../standard-library/ios-functions.md#uppercase)為非零, 取代為 。  & 

- 否則，轉換規格會是 **lg**。 如果 **iosbase**. **標誌** & **ios_base:大寫**是非`g`零,`G`取代為 。

如果 **iosbase**. **標誌** & **ios_base::固定**為非零或**如果 iosbase**。 [precision](../standard-library/ios-base-class.md#precision) 大於零，就會在轉換規格前面加上值為 **iosbase**. **precision** 的有效位數。 所有填補行為都與整數輸出欄位的填補行為相同。 填補字元為 **fill**。 最後：

- 如果 **iosbase**. **flags**標誌 顯示波 是非零**+**,標誌 已準備到轉換規範。[showpos](../standard-library/ios-functions.md#showpos)  & `ios_base::`

- 如果 **iosbase**. **flags**標誌 顯示[點是](../standard-library/ios-functions.md#showpoint)非零**#**,標誌 已準備到轉換規範。`ios_base::`  & 

第四個虛擬的受保護成員函式：

```cpp
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,
    CharType _Fill,
    long double val) const;
```

第三個表示相同,只不過轉換規範中的修`l`飾字取代`L`為 。

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

行為行為與第一個相同,只不過它生成從*val*生成的布爾輸出欄位。

布林值輸出欄位採用下列兩種形式其中之一。 如果`iosbase.flags & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) **為 false**,`do_put(_Next, _Iosbase, _Fill, (long)val)`則成員函數將傳回 ,這通常生成序列為 0( 對於**false)** 或 1(對於**true)。** 否則,產生的序列為*fac*。[假名](../standard-library/numpunct-class.md#falsename)(**為虛假**名稱) 或*fac*。[真名](../standard-library/numpunct-class.md#truename)(**為 true)。**

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

## <a name="num_putiter_type"></a><a name="iter_type"></a>num_put:iter_type

描述輸出迭代器的類型。

```cpp
typedef OutputIterator iter_type;
```

### <a name="remarks"></a>備註

類型是範本參數**輸出反覆運算器**的同義詞。

## <a name="num_putnum_put"></a><a name="num_put"></a>num_put::num_put

`num_put` 類型物件的建構函式。

```cpp
explicit num_put(size_t _Refs = 0);
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

建構函數用區域設置初始化其基本物件 **::**[分面](../standard-library/locale-class.md#facet_class)(= *Refs*)。

## <a name="num_putput"></a><a name="put"></a>num_put::p烏特

將數位轉換為表示給定區域設定格式`CharType`的數位的序列。

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

*瓦爾*\
要輸出的數字或布林值類型。

### <a name="return-value"></a>傳回值

輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。

### <a name="remarks"></a>備註

所有成員函數傳[回](#do_put)`next`do_put `_Iosbase` `_Fill` `val`(、 、 、 、

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

[\<區域設定>](../standard-library/locale.md)\
[分面類](../standard-library/locale-class.md#facet_class)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
