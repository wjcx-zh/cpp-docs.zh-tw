---
title: codecvt 類別
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::codecvt
- xlocale/std::codecvt::extern_type
- xlocale/std::codecvt::intern_type
- xlocale/std::codecvt::state_type
- xlocale/std::codecvt::always_noconv
- xlocale/std::codecvt::do_always_noconv
- xlocale/std::codecvt::do_encoding
- xlocale/std::codecvt::do_in
- xlocale/std::codecvt::do_length
- xlocale/std::codecvt::do_max_length
- xlocale/std::codecvt::do_out
- xlocale/std::codecvt::do_unshift
- xlocale/std::codecvt::encoding
- xlocale/std::codecvt::in
- xlocale/std::codecvt::length
- xlocale/std::codecvt::max_length
- xlocale/std::codecvt::out
- xlocale/std::codecvt::unshift
helpviewer_keywords:
- std::codecvt [C++]
- std::codecvt [C++], extern_type
- std::codecvt [C++], intern_type
- std::codecvt [C++], state_type
- std::codecvt [C++], always_noconv
- std::codecvt [C++], do_always_noconv
- std::codecvt [C++], do_encoding
- std::codecvt [C++], do_in
- std::codecvt [C++], do_length
- std::codecvt [C++], do_max_length
- std::codecvt [C++], do_out
- std::codecvt [C++], do_unshift
- std::codecvt [C++], encoding
- std::codecvt [C++], in
- std::codecvt [C++], length
- std::codecvt [C++], max_length
- std::codecvt [C++], out
- std::codecvt [C++], unshift
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
ms.openlocfilehash: 77af6b627847dbb16523c247f03f58e30aeef236
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87230126"
---
# <a name="codecvt-class"></a>codecvt 類別

類別樣板，描述可做為地區設定 facet 的物件。 它可以控制程式內部字元編碼的值序列和程式外部字元編碼的值序列之間的轉換。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>參數

*CharType*\
用於程式內部字元編碼的類型。

*節*\
用於程式外部字元編碼的類型。

*StateType*\
類型，可以用來表示字元表示的內部和外部類型之間的轉換中繼狀態。

## <a name="remarks"></a>備註

類別樣板描述可以做為[地區設定 facet](../standard-library/locale-class.md#facet_class)的物件，以控制*CharType*類型的值序列與*Byte*類型的值序列之間的轉換。 類別*StateType*會區分轉換的特性，而*StateType*類別的物件會在轉換期間儲存任何必要的狀態資訊。

內部編碼使用的標記法具有每個字元的固定位元組數，通常是類型 **`char`** 或類型 **`wchar_t`** 。

如同所有地區設定 facet，靜態物件 `id` 有初始儲存值零。 第一次嘗試存取其預存值時，會在 `id` 中儲存唯一的正值。

[do_in](#do_in) 和 [do_out](#do_out) 的樣板版本一律會傳回 `codecvt_base::noconv`。

C++ 標準程式庫定義數個明確特製化：

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

在 **`wchar_t`** 和序列之間轉換 **`char`** 。

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

在 **`char16_t`** 編碼為 utf-16 的序列和 **`char`** 編碼為 utf-8 的序列之間轉換。

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

在 **`char32_t`** 編碼為 utf-32 （UCS-4）的序列和 **`char`** 編碼為 utf-8 的序列之間轉換。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[codecvt](#codecvt)|做為地區設定 facet 處理轉換之 `codecvt` 類別物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[extern_type](#extern_type)|用於外部表示的字元類型。|
|[intern_type](#intern_type)|用於內部表示的字元類型。|
|[state_type](#state_type)|字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[always_noconv](#always_noconv)|測試是否不需要完成轉換。|
|[do_always_noconv](#do_always_noconv)|虛擬函式，呼叫以測試是否不需要完成轉換。|
|[do_encoding](#do_encoding)|虛擬函式，測試資料流程的編碼 `Byte` 是否與狀態相關，所 `Byte` 使用值與產生的值之間的比率是否 `CharType` 為常數，如果是的話，則決定該比率的值。|
|[do_in](#do_in)|虛擬函式，呼叫以將內部值的序列轉換成 `Byte` 外部值的序列 `CharType` 。|
|[do_length](#do_length)|虛擬函式，用來判斷 `Byte` 指定的外部值序列中有多少個值 `Byte` 不會產生超過指定數目的內部 `CharType` 值，並傳回該數目的 `Byte` 值。|
|[do_max_length](#do_max_length)|虛擬函式，傳回產生一個內部 `CharType` 所需的外部 Byte 數目上限。|
|[do_out](#do_out)|虛擬函式，呼叫以將內部值的序列轉換成 `CharType` 外部位元組序列。|
|[do_unshift](#do_unshift)|虛擬函式，呼叫以提供 `Byte` 狀態相關轉換所需的值，以完成值序列中的最後一個字元 `Byte` 。|
|[編碼](#encoding)|測試資料流程的編碼是否與 `Byte` 狀態相關，所 `Byte` 使用值與產生的值之間的比率是否 `CharType` 為常數，如果是的話，則決定該比率的值。|
|[in](#in)|將值序列的外部表示轉換 `Byte` 成值序列的內部標記法 `CharType` 。|
|[length](#length)|判斷 `Byte` 指定的外部值序列中有多少值 `Byte` 不會產生超過指定數目的內部 `CharType` 值，並傳回該數目的 `Byte` 值。|
|[max_length](#max_length)|傳回 `Byte` 產生一個內部所需的最大外部值數目 `CharType` 。|
|[脫銷](#out)|將內部值的序列轉換 `CharType` 成外部值的序列 `Byte` 。|
|[unshift](#unshift)|提供 `Byte` 狀態相關轉換所需的外部值，以完成值序列中的最後一個字元 `Byte` 。|

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>codecvt：： always_noconv

測試是否不需要進行任何轉換。

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

布林值， **`true`** 如果不需要進行任何轉換，則為; **`false`** 如果至少有一個必須完成，則為。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_always_noconv](#do_always_noconv)。

### <a name="example"></a>範例

```cpp
// codecvt_always_noconv.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result1 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;

   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).always_noconv( );

   if ( result2 )
      cout << "No conversion is needed." << endl;
   else
      cout << "At least one conversion is required." << endl;
}
```

```Output
No conversion is needed.
At least one conversion is required.
```

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>codecvt：： codecvt

作為地區設定 Facet 處理轉換之 codecvt 類別物件的建構函式。

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>參數

*參照*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*Refs*參數的可能值和其重要性如下：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- 2：未定義這些值。

此函式會 `locale::facet` 使用[locale：： facet](../standard-library/locale-class.md#facet_class)初始化其基底物件 `(refs)` 。

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>codecvt：:d o_always_noconv

虛擬函式，呼叫以測試是否不需要進行任何轉換。

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

**`true`** 只有在[do_in](#do_in)或[do_out](#do_out)的每個呼叫傳回時，受保護的虛擬成員函式才會傳回 `noconv` 。

範本版本一律會傳回 **`true`** 。

### <a name="example"></a>範例

請參閱呼叫 [always_noconv](#always_noconv) 的範例，其會呼叫 `do_always_noconv`。

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>codecvt：:d o_encoding

虛擬函式，測試資料流程的編碼 `Byte` 是否與狀態相關，所 `Byte` 使用值與產生的值之間的比率是否 `CharType` 為常數，如果是，則決定該比率的值。

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>傳回值

此受保護的虛擬成員函式會傳回：

- -1，如果類型的序列編碼 `extern_type` 與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N* (如果編碼只與長度為 *N* 的序列有關)

### <a name="example"></a>範例

請參閱 [encoding](#encoding) 的範例，其會呼叫 `do_encoding`。

## <a name="codecvtdo_in"></a><a name="do_in"></a>codecvt：:d o_in

虛擬函式，呼叫以將外部值的序列轉換成 `Byte` 內部值的序列 `CharType` 。

```cpp
virtual result do_in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
要轉換之序列開頭的指標。

*last1*\
要轉換之序列結尾的指標。

*next1*\
超過已轉換序列結尾之第一個未轉換字元的指標。

*first2*\
已轉換序列開頭的指標。

*last2*\
已轉換序列結尾的指標。

*next2*\
`CharType`最後一次轉換後 `CharType` ，指向目的地序列中第一個未修改字元的指標。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error`如果來源序列的格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功，則為。

- `codecvt_base::partial`如果來源不足或目的地不夠大，轉換就會成功。

### <a name="remarks"></a>備註

*狀態*必須代表新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [in](#in) 的範例，其會呼叫 `do_in`。

## <a name="codecvtdo_length"></a><a name="do_length"></a>codecvt：:d o_length

虛擬函式，用來判斷 `Byte` 指定的外部值序列中有多少個值 `Byte` 不會產生超過指定數目的內部 `CharType` 值，並傳回該數目的 `Byte` 值。

```cpp
virtual int do_length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
外部序列開頭的指標。

*last1*\
外部序列結尾的指標。

*len2*\
成員函式可以傳回的最大 `Byte` 值數目。

### <a name="return-value"></a>傳回值

整數，代表位於 [，）之外部來源序列所定義之轉換數目上限的計數，而不大於*len2* `first1` `last1` 。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會有效地呼叫 `do_in( state, first1, last1, next1, buf, buf + len2, next2)` *狀態*（狀態的複本）、某些緩衝區 `buf` ，以及指標 `next1` 和 `next2` 。

然後，它會傳回 `next2`  -  `buf` 。 因此，它會計算來源序列在 [，）所定義*len2*的轉換數目上限，而不大於 len2 `first1` `last1` 。

範本版本一律會傳回*last1*  -  *first1*和*len2*的較小者。

### <a name="example"></a>範例

請參閱[長度](#length)的範例，其會呼叫 `do_length` 。

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>codecvt：:d o_max_length

虛擬函式，會傳回 `Byte` 產生一個內部所需的最大外部值數目 `CharType` 。

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>傳回值

`Byte`產生一個所需的最大值數目 `CharType` 。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會傳回最大的允許值，可由[do_length](#do_length) `( first1, last1, 1)` 的任意有效值*first1*和*last1*。

### <a name="example"></a>範例

請參閱 [max_length](#max_length) 的範例，其會呼叫 `do_max_length`。

## <a name="codecvtdo_out"></a><a name="do_out"></a>codecvt：:d o_out

虛擬函式，呼叫以將內部值的序列轉換成 `CharType` 外部值的序列 `Byte` 。

```cpp
virtual result do_out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
要轉換之序列開頭的指標。

*last1*\
要轉換之序列結尾的指標。

*next1*\
`CharType`上次轉換後，第一個未轉換的指標的參考 `CharType` 。

*first2*\
已轉換序列開頭的指標。

*last2*\
已轉換序列結尾的指標。

*next2*\
`Byte`上次轉換後，第一個未轉換的指標的參考 `Byte` 。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果來源序列的格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功，則為。

- `codecvt_base::partial`如果來源不足，或目的地的大小不足以讓轉換成功。

### <a name="remarks"></a>備註

*狀態*必須代表新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [out](#out) 的範例，其會呼叫 `do_out`。

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>codecvt：:d o_unshift

虛擬函式，呼叫以提供 `Byte` 狀態相關轉換所需的值，以完成值序列中的最後一個字元 `Byte` 。

```cpp
virtual result do_unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first2*\
目的範圍中第一個位置的指標。

*last2*\
目的範圍中最後一個位置的指標。

*next2*\
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果*狀態*代表無效狀態

- `codecvt_base::noconv` (如果函式不會執行任何轉換)

- `codecvt_base::ok`如果轉換成功

- `codecvt_base::partial`如果目的地不夠大，無法成功轉換

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試將 source 元素 `CharType` （0）轉換成它儲存在 [，）內的目的地序列 `first2` `last2` ，但終止專案除外 `Byte` （0）。 它一律會在*next2*中儲存目的地序列中第一個未改變元素的指標。

_ *State* 必須是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 一般來說，轉換 source 元素 `CharType` （0）會讓目前狀態保持在初始轉換狀態。

### <a name="example"></a>範例

請參閱 [unshift](#unshift) 的範例，其會呼叫 `do_unshift`。

## <a name="codecvtencoding"></a><a name="encoding"></a>codecvt：： encoding

測試資料流程的編碼是否與 `Byte` 狀態相關，所 `Byte` 使用值與產生的值之間的比率是否 `CharType` 為常數，如果是的話，則決定該比率的值。

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>傳回值

如果傳回值是正數，該值就是 `Byte` 產生字元所需的常字元數 `CharType` 。

此受保護的虛擬成員函式會傳回：

- -1，如果類型的序列編碼 `extern_type` 與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N*，如果編碼只涉及長度為 N 的序列 *。*

### <a name="remarks"></a>備註

此成員函式會傳回 [do_encoding](#do_encoding)。

### <a name="example"></a>範例

```cpp
// codecvt_encoding.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc ( "German_Germany" );
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );
   cout << result1 << endl;
}
```

```Output
1
1
1
```

## <a name="codecvtextern_type"></a><a name="extern_type"></a>codecvt：： extern_type

用於外部表示的字元類型。

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Byte` 的同義字。

## <a name="codecvtin"></a><a name="in"></a>codecvt：： in

將值序列的外部表示轉換 `Byte` 成值序列的內部標記法 `CharType` 。

```cpp
result in(
    StateType& state,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
要轉換之序列開頭的指標。

*last1*\
要轉換之序列結尾的指標。

*next1*\
超過已轉換序列結尾之第一個未轉換字元的指標。

*first2*\
已轉換序列開頭的指標。

*last2*\
已轉換序列結尾的指標。

*next2*\
指向 `CharType` 最後一次轉換 `Chartype` 成目的地序列中第一個未修改的字元之後的的指標。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error`如果來源序列的格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功，則為。

- `codecvt_base::partial`如果來源不足，或目的地的大小不足以讓轉換成功。

### <a name="remarks"></a>備註

*狀態*必須代表新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 在部分轉換之後，必須將*狀態*設定為，以允許在新字元到達時繼續轉換。

此成員函式會傳回[do_in](#do_in) `( state, first1,  last1,  next1, first2, last2,  next2)` 。

### <a name="example"></a>範例

```cpp
// codecvt_in.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string to be converted!";
   wchar_t pwszInt [LEN+1];
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));
   const char* pszNext;
   wchar_t* pwszNext;
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).in( state,
          pszExt, &pszExt[strlen(pszExt)], pszNext,
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );
   pwszInt[strlen(pszExt)] = 0;
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )
   << L"The converted string is:\n ["
   << &pwszInt[0]
   << L"]" << endl;
   exit(-1);
}
```

```Output
It worked! The converted string is:
[This is the string to be converted!]
```

## <a name="codecvtintern_type"></a><a name="intern_type"></a>codecvt：： intern_type

用於內部表示的字元類型。

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

## <a name="codecvtlength"></a><a name="length"></a>codecvt：： length

判斷 `Byte` 指定的外部值序列中有多少值 `Byte` 不會產生超過指定數目的內部 `CharType` 值，並傳回該數目的 `Byte` 值。

```cpp
int length(
    const StateType& state,
    const Byte* first1,
    const Byte* last1,
    size_t len2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
外部序列開頭的指標。

*last1*\
外部序列結尾的指標。

*len2*\
可由成員函式傳回的位元組數目上限。

### <a name="return-value"></a>傳回值

整數，代表位於 [，）之外部來源序列所定義之轉換數目上限的計數，而不大於*len2* `first1` `last1` 。

### <a name="remarks"></a>備註

此成員函式會傳回[do_length](#do_length) `( state, first1, last1, len2)` 。

### <a name="example"></a>範例

```cpp
// codecvt_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;
#define LEN 90
int main( )
{
   char* pszExt = "This is the string whose length is to be measured!";
   mbstate_t state = {0};
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
     ( loc ).length( state,
          pszExt, &pszExt[strlen(pszExt)], LEN );
   cout << "The length of the string is: ";
   wcout << res;
   cout << "." << endl;
   exit(-1);
}
```

```Output
The length of the string is: 50.
```

## <a name="codecvtmax_length"></a><a name="max_length"></a>codecvt：： max_length

傳回 `Byte` 產生一個內部所需的最大外部值數目 `CharType` 。

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>傳回值

`Byte`產生一個所需的最大值數目 `CharType` 。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_max_length](#do_max_length)。

### <a name="example"></a>範例

```cpp
// codecvt_max_length.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc( "C");//English_Britain" );//German_Germany
   int res = use_facet<codecvt<char, char, mbstate_t> >
     ( loc ).max_length( );
   wcout << res << endl;
}
```

```Output
1
```

## <a name="codecvtout"></a><a name="out"></a>codecvt：： out

將內部值的序列轉換 `CharType` 成外部值的序列 `Byte` 。

```cpp
result out(
    StateType& state,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first1*\
要轉換之序列開頭的指標。

*last1*\
要轉換之序列結尾的指標。

*next1*\
上次轉換後第一個未轉換的指標參考 `CharType` `CharType` 。

*first2*\
已轉換序列開頭的指標。

*last2*\
已轉換序列結尾的指標。

*next2*\
上次轉換後第一個未轉換的指標參考 `Byte` `Byte` 。

### <a name="return-value"></a>傳回值

此成員函式會傳回[do_out](#do_out) `( state, first1, last1, next1, first2, last2, next2)` 。

### <a name="remarks"></a>備註

如需詳細資訊，請參閱 [codecvt::do_out](#do_out)。

### <a name="example"></a>範例

```cpp
// codecvt_out.cpp
// compile with: /EHsc
#define _INTL
#include <locale>
#include <iostream>
#include <wchar.h>
using namespace std;
#define LEN 90
int main( )
{
   char pszExt[LEN+1];
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );
   char* pszNext;
   const wchar_t* pwszNext;
   mbstate_t state;
   locale loc("C");//English_Britain");//German_Germany
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >
      ( loc ).out( state,
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );
   pszExt[wcslen( pwszInt )] = 0;
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )
   << "The converted string is:\n ["
   << &pszExt[0]
   << "]" << endl;
}
```

```Output
It worked: The converted string is:
[This is the wchar_t string to be converted.]
```

## <a name="codecvtstate_type"></a><a name="state_type"></a>codecvt：： state_type

字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `StateType` 的同義字。

## <a name="codecvtunshift"></a><a name="unshift"></a>codecvt：： unshift

提供 `Byte` 狀態相關轉換所需的值，以完成值序列中的最後一個字元 `Byte` 。

```cpp
result unshift(
    StateType& state,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*狀態*\
成員函式呼叫之間所保留的轉換狀態。

*first2*\
目的範圍中第一個位置的指標。

*last2*\
目的範圍中最後一個位置的指標。

*next2*\
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果狀態代表不正確狀態。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功，則為。

- `codecvt_base::partial`如果目的地不夠大，所以轉換成功。

### <a name="remarks"></a>備註

受保護的虛擬成員函式會嘗試將 source 元素 `CharType` （0）轉換成它儲存在 [，）內的目的地序列 `first2` `last2` ，但終止專案除外 `Byte` （0）。 它一律會在*next2*中儲存目的地序列中第一個未改變元素的指標。

*狀態*必須代表新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 一般來說，轉換 source 元素 `CharType` （0）會讓目前狀態保持在初始轉換狀態。

此成員函式會傳回[do_unshift](#do_unshift) `( state, first2, last2, next2 )` 。

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)\
[字碼頁](../c-runtime-library/code-pages.md)\
[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
