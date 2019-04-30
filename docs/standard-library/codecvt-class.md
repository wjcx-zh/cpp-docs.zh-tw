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
ms.openlocfilehash: be1075da65284ac3f9672a839622b59c8926bfb9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405232"
---
# <a name="codecvt-class"></a>codecvt 類別

樣板類別，描述可做為地區設定 facet 的物件。 它可以控制程式內部字元編碼的值序列和程式外部字元編碼的值序列之間的轉換。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>參數

*CharType*<br/>
用於程式內部字元編碼的類型。

*Byte*<br/>
用於程式外部字元編碼的類型。

*StateType*<br/>
類型，可以用來表示字元表示的內部和外部類型之間的轉換中繼狀態。

## <a name="remarks"></a>備註

此範本類別描述可以做為物件[地區設定 facet](../standard-library/locale-class.md#facet_class)，以控制類型的值序列之間的轉換*CharType*類型的值序列和*位元組*. 此類別*StateType*特性轉換-和類別的物件*StateType*會儲存在轉換期間任何必要的狀態資訊。

內部編碼使用表示搭配固定的每個字元的位元組數輸入通常**char**或型別**wchar_t**。

如同所有地區設定 facet，靜態物件 `id` 有初始儲存值零。 第一次嘗試存取其預存值時，會在 `id` 中儲存唯一的正值。

[do_in](#do_in) 和 [do_out](#do_out) 的樣板版本一律會傳回 `codecvt_base::noconv`。

C++ 標準程式庫定義數個明確特製化：

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

之間轉換**wchar_t**並**char**序列。

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

之間轉換`char16_t`編碼為 utf-16 的順序並**char**序列編碼為 utf-8。

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

之間轉換`char32_t`序列編碼為 UTF-32 (ucs-4) 和**char**序列編碼為 utf-8。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[codecvt](#codecvt)|做為地區設定 facet 處理轉換之 `codecvt` 類別物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[extern_type](#extern_type)|用於外部表示的字元類型。|
|[intern_type](#intern_type)|用於內部表示的字元類型。|
|[state_type](#state_type)|字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。|

### <a name="member-functions"></a>成員函式

|成員函式|描述|
|-|-|
|[always_noconv](#always_noconv)|測試是否不需要完成轉換。|
|[do_always_noconv](#do_always_noconv)|虛擬函式，呼叫以測試是否不需要完成轉換。|
|[do_encoding](#do_encoding)|虛擬函式，測試 `Byte` 資料流的編碼方式是否為狀態相關，所用的 `Byte` 和所產生的 `CharType` 之間的比率是否為常數，而且，如果是的話，判斷該比率的值。|
|[do_in](#do_in)|虛擬函式，呼叫以將內部 `Byte` 序列轉換為外部 `CharType` 序列。|
|[do_length](#do_length)|虛擬函式，判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。|
|[do_max_length](#do_max_length)|虛擬函式，傳回產生一個內部 `CharType` 所需的外部 Byte 數目上限。|
|[do_out](#do_out)|虛擬函式，呼叫以將內部 `CharType` 序列轉換為外部 Byte 序列。|
|[do_unshift](#do_unshift)|虛擬函式，呼叫以提供狀態相關轉換所需的 `Byte`，以完成 `Byte` 序列的最後一個字元。|
|[encoding](#encoding)|測試 `Byte` 資料流的編碼方式是否為狀態相關，所用的 `Byte` 和所產生的 `CharType` 之間的比率是否為常數，而且，如果是的話，判斷該比率的值。|
|[in](#in)|將 `Byte` 序列的外部表示轉換為 `CharType` 序列的內部表示。|
|[length](#length)|判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。|
|[max_length](#max_length)|傳回產生一個內部 `Byte` 所需的外部 `CharType` 數目上限。|
|[out](#out)|將內部 `CharType` 序列轉換為外部 `Byte` 序列。|
|[unshift](#unshift)|提供狀態相關轉換所需的 `Byte`，以完成 `Byte` 序列的最後一個字元。|

## <a name="requirements"></a>需求

**標頭︰**\<locale>

**命名空間：** std

## <a name="always_noconv"></a>  codecvt::always_noconv

測試是否不需要完成轉換。

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

如果不需要完成任何轉換，則為布林值 **true**；如果至少需要完成一個轉換，則為 **false**。

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

## <a name="codecvt"></a>  codecvt::codecvt

作為地區設定 Facet 處理轉換之 codecvt 類別物件的建構函式。

```cpp
explicit codecvt(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*<br/>
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

可能值 *_Refs*參數和其意義如下：

- 0:物件的存留期是由包含它的地區設定管理。

- 1:物件的存留期必須以手動方式管理。

- 2:未定義這些值。

建構函式會初始化其`locale::facet`與基底物件**地區設定::**[facet](../standard-library/locale-class.md#facet_class)(`_Refs`)。

## <a name="do_always_noconv"></a>  codecvt::do_always_noconv

虛擬函式，呼叫以測試是否不需要完成轉換。

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

受保護虛擬成員函式會傳回 **，則為 true**只有當每次呼叫[do_in](#do_in)或是[do_out](#do_out)傳回`noconv`。

樣板版本一律會傳回 **true**。

### <a name="example"></a>範例

請參閱呼叫 [always_noconv](#always_noconv) 的範例，其會呼叫 `do_always_noconv`。

## <a name="do_encoding"></a>  codecvt::do_encoding

如果所測試的虛擬函式的編碼方式`Byte`資料流是否為狀態相關，之間的比率`Byte`使用的秒和`CharType`產生會為常數，而且如果是的話，判斷該比率的值。

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>傳回值

此受保護的虛擬成員函式會傳回：

- -1，如果型別的序列的編碼`extern_type`與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N* (如果編碼只與長度為 *N* 的序列有關)

### <a name="example"></a>範例

請參閱 [encoding](#encoding) 的範例，其會呼叫 `do_encoding`。

## <a name="do_in"></a>  codecvt::do_in

虛擬函式，呼叫以將轉換為外部`Byte`的內部序列`CharType`s。

```cpp
virtual result do_in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
要轉換之序列開頭的指標。

*last1*<br/>
要轉換之序列結尾的指標。

*next1*<br/>
超過已轉換序列結尾之第一個未轉換字元的指標。

*first2*<br/>
已轉換序列開頭的指標。

*last2*<br/>
已轉換序列結尾的指標。

*next2*<br/>
指標`CharType`所附在上一個轉換之後`CharType`，目的序列中的第一個未變更的字元。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error` 如果來源序列的格式不，正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok` 如果轉換成功。

- `codecvt_base::partial` 如果來源不足，或目的地是沒有夠大，才能成功轉換。

### <a name="remarks"></a>備註

*_State*必須代表是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [in](#in) 的範例，其會呼叫 `do_in`。

## <a name="do_length"></a>  codecvt::do_length

虛擬函式，判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。

```cpp
virtual int do_length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
外部序列開頭的指標。

*last1*<br/>
外部序列結尾的指標。

*_Len2*<br/>
最大數目`Byte`的成員函式可傳回。

### <a name="return-value"></a>傳回值

整數，表示轉換，不大於最大數目的計數 *_Len2*外部來源序列所定義、 [ `first1`， `last1`)。

### <a name="remarks"></a>備註

受保護虛擬成員函式會有效地呼叫`do_in`( `_State`， `first1`， `last1`， `next1`， `_Buf`， `_Buf`  +  `_Len2`， `next2`) 針對 *_State* （狀態的複本），某些緩衝區`_Buf`，和指標`next1`和`next2`。

然後它會傳回`next2`  -  `buf`。 因此，它會計算的轉換，不大於最大數目 *_Len2*來源序列所定義、 [ `first1`， `last1`)。

樣板版本一律會傳回較小的數目*last1* - *first1*並 *_Len2*。

### <a name="example"></a>範例

範例，請參閱[長度](#length)，其會呼叫`do_length`。

## <a name="do_max_length"></a>  codecvt::do_max_length

傳回外部最大數目的虛擬函式`Byte`產生一個內部所需`CharType`。

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>傳回值

最大數目`Byte`產生一個所需`CharType`。

### <a name="remarks"></a>備註

受保護虛擬成員函式會傳回可傳回的最大允許值[do_length](#do_length)( `first1`， `last1`，1) 的任意有效值*first1*並*last1*。

### <a name="example"></a>範例

請參閱 [max_length](#max_length) 的範例，其會呼叫 `do_max_length`。

## <a name="do_out"></a>  codecvt::do_out

虛擬函式，呼叫以將內部 `CharType` 序列轉換為外部 `Byte` 序列。

```cpp
virtual result do_out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
要轉換之序列開頭的指標。

*last1*<br/>
要轉換之序列結尾的指標。

*next1*<br/>
第一個指標參考轉換`CharType`，最後一個之後`CharType`轉換。

*first2*<br/>
已轉換序列開頭的指標。

*last2*<br/>
已轉換序列結尾的指標。

*next2*<br/>
第一個指標參考轉換`Byte`，最後一個之後`Byte`轉換。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error` 如果來源序列的格式不，正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok` 如果轉換成功。

- `codecvt_base::partial` 如果來源不足，或目的地的逸出序列並不夠大，才能成功轉換。

### <a name="remarks"></a>備註

*_State*必須代表是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [out](#out) 的範例，其會呼叫 `do_out`。

## <a name="do_unshift"></a>  codecvt::do_unshift

虛擬函式，呼叫以提供狀態相關轉換所需的 `Byte`，以完成 `Byte` 序列的最後一個字元。

```cpp
virtual result do_unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first2*<br/>
目的範圍中第一個位置的指標。

*last2*<br/>
目的範圍中最後一個位置的指標。

*next2*<br/>
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error` 如果 _*狀態*表示無效的狀態

- `codecvt_base::noconv` (如果函式不會執行任何轉換)

- `codecvt_base::ok` 如果轉換成功

- `codecvt_base::partial` 如果目的地無法夠大，才能成功轉換

### <a name="remarks"></a>備註

受保護虛擬成員函式會嘗試將轉換的來源元素`CharType`(0) 的目的序列儲存在 [ `first2`， `last2`)，除了終端項目`Byte`(0)。 它一律會儲存在*next2*指向目的序列中第一個未變更的元素。

_ *State* 必須是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 一般而言，轉換的來源項目`CharType`(0) 的初始轉換狀態中離開目前的狀態。

### <a name="example"></a>範例

請參閱 [unshift](#unshift) 的範例，其會呼叫 `do_unshift`。

## <a name="encoding"></a>  codecvt::encoding

測試 `Byte` 資料流的編碼方式是否為狀態相關，所用的 `Byte` 和所產生的 `CharType` 之間的比率是否為常數，而且，如果是的話，判斷該比率的值。

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>傳回值

如果傳回的值為正數，則該值是固定數目`Byte`以產生所需字元`CharType`字元。

此受保護的虛擬成員函式會傳回：

- -1，如果型別的序列的編碼`extern_type`與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N* (如果編碼只與長度為 *N* 的序列有關)。

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

## <a name="extern_type"></a>  codecvt::extern_type

用於外部表示的字元類型。

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `Byte`的同義字。

## <a name="in"></a>  codecvt::in

將 `Byte` 序列的外部表示轉換為 `CharType` 序列的內部表示。

```cpp
result in(
    StateType& _State,
    const Byte* first1,
    const Byte* last1,
    const Byte*& next1,
    CharType* first2,
    CharType* last2,
    CharType*& next2,) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
要轉換之序列開頭的指標。

*last1*<br/>
要轉換之序列結尾的指標。

*next1*<br/>
超過已轉換序列結尾之第一個未轉換字元的指標。

*first2*<br/>
已轉換序列開頭的指標。

*last2*<br/>
已轉換序列結尾的指標。

*next2*<br/>
指標`CharType`所附在上一個轉換之後`Chartype`目的序列中的第一個未變更的字元。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error` 如果來源序列的格式不，正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok` 如果轉換成功。

- `codecvt_base::partial` 如果來源不足，或目的地的逸出序列並不夠大，才能成功轉換。

### <a name="remarks"></a>備註

*_State*必須代表是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 部分轉換後, *_State*必須設為允許新字元到達時繼續轉換。

此成員函式會傳回 [do_in](#do_in)( `_State`, _ *First1,  last1,  next1, First2, _Llast2,  next2*)。

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

## <a name="intern_type"></a>  codecvt::intern_type

用於內部表示的字元類型。

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `CharType`的同義字。

## <a name="length"></a>  codecvt::length

判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。

```cpp
int length(
    const StateType& _State,
    const Byte* first1,
    const Byte* last1,
    size_t _Len2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
外部序列開頭的指標。

*last1*<br/>
外部序列結尾的指標。

*_Len2*<br/>
可由成員函式傳回的位元組數目上限。

### <a name="return-value"></a>傳回值

整數，表示轉換，不大於最大數目的計數 *_Len2*外部來源序列所定義、 [ `first1`， `last1`)。

### <a name="remarks"></a>備註

此成員函式會傳回 [do_length](#do_length)( *_State,  first1*, `last1`, `_Len2`)。

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

## <a name="max_length"></a>  codecvt::max_length

傳回產生一個內部 `Byte` 所需的外部 `CharType` 數目上限。

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>傳回值

最大數目`Byte`產生一個所需`CharType`。

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

## <a name="out"></a>  codecvt::out

將內部 `CharType` 序列轉換為外部 `Byte` 序列。

```cpp
result out(
    StateType& _State,
    const CharType* first1,
    const CharType* last1,
    const CharType*& next1,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first1*<br/>
要轉換之序列開頭的指標。

*last1*<br/>
要轉換之序列結尾的指標。

*next1*<br/>
第一個指標參考轉換`CharType`最後一個之後`CharType`轉換。

*first2*<br/>
已轉換序列開頭的指標。

*last2*<br/>
已轉換序列結尾的指標。

*next2*<br/>
第一個指標參考轉換`Byte`在上一個轉換之後`Byte`。

### <a name="return-value"></a>傳回值

此成員函式會傳回 [do_out](#do_out)( `_State`, `first1`, `last1`, `next1`, `first2`, `last2`, `next2`)。

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

## <a name="state_type"></a>  codecvt::state_type

字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 `StateType`的同義字。

## <a name="unshift"></a>  codecvt::unshift

提供`Byte`若要完成之序列中的最後一個字元狀態相關轉換所需的 s `Byte`s。

```cpp
result unshift(
    StateType& _State,
    Byte* first2,
    Byte* last2,
    Byte*& next2) const;
```

### <a name="parameters"></a>參數

*_State*<br/>
成員函式呼叫之間所保留的轉換狀態。

*first2*<br/>
目的範圍中第一個位置的指標。

*last2*<br/>
目的範圍中最後一個位置的指標。

*next2*<br/>
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error` 如果狀態表示無效的狀態。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok` 如果轉換成功。

- `codecvt_base::partial` 如果目的地無法夠大，才能成功轉換。

### <a name="remarks"></a>備註

受保護虛擬成員函式會嘗試將轉換的來源元素`CharType`(0) 的目的序列儲存在 [ `first2`， `last2`)，除了終端項目`Byte`(0)。 它一律會儲存在*next2*指向目的序列中第一個未變更的元素。

*_State*必須代表是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 一般而言，轉換的來源項目`CharType`(0) 的初始轉換狀態中離開目前的狀態。

此成員函式會傳回 [do_unshift](#do_unshift)( `_State`, `first2`, `last2`, `next2` )。

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)<br/>
[字碼頁](../c-runtime-library/code-pages.md)<br/>
[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
