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
ms.openlocfilehash: 3dba971b112c23325e0529e53746cbee827df5e9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371957"
---
# <a name="codecvt-class"></a>codecvt 類別

描述可用作區域設置面的物件的類範本。 它可以控制程式內部字元編碼的值序列和程式外部字元編碼的值序列之間的轉換。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class Byte, class StateType>
class codecvt : public locale::facet, codecvt_base;
```

### <a name="parameters"></a>參數

*字元類型*\
用於程式內部字元編碼的類型。

*位元組*\
用於程式外部字元編碼的類型。

*狀態類型*\
類型，可以用來表示字元表示的內部和外部類型之間的轉換中繼狀態。

## <a name="remarks"></a>備註

類範本描述一個可以用作[區域設置面](../standard-library/locale-class.md#facet_class)的物件,以控制*CharType 類型的*值序列和*位元*組 類型的值序列之間的轉換。 類*StateType*是轉換的特徵 - 類別*StateType*的物件在轉換期間儲存任何必要的狀態資訊。

內部編碼使用每個字元具有固定數量的位元組的表示形式,通常鍵入**char**或鍵入**wchar_t**。

如同所有地區設定 facet，靜態物件 `id` 有初始儲存值零。 第一次嘗試存取其預存值時，會在 `id` 中儲存唯一的正值。

[do_in](#do_in) 和 [do_out](#do_out) 的樣板版本一律會傳回 `codecvt_base::noconv`。

C++ 標準程式庫定義數個明確特製化：

```cpp
template<>
codecvt<wchar_t, char, mbstate_t>
```

**在wchar_t**序列和**字元**序列之間進行轉換。

```cpp
template<>
codecvt<char16_t, char, mbstate_t>
```

在編碼為`char16_t`UTF-16 的序列和編碼為 UTF-8 的**字元**序列之間進行轉換。

```cpp
template<>
codecvt<char32_t, char, mbstate_t>
```

在編碼為`char32_t`UTF-32 (UCS-4) 的序列和編碼為 UTF-8 的**字元**序列之間進行轉換。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[編解碼](#codecvt)|做為地區設定 facet 處理轉換之 `codecvt` 類別物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[extern_type](#extern_type)|用於外部表示的字元類型。|
|[intern_type](#intern_type)|用於內部表示的字元類型。|
|[state_type](#state_type)|字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[always_noconv](#always_noconv)|測試是否不需要完成轉換。|
|[do_always_noconv](#do_always_noconv)|虛擬函式，呼叫以測試是否不需要完成轉換。|
|[do_encoding](#do_encoding)|測試`Byte`流的編碼是否取決於狀態、`Byte`使用的值與生成`CharType`的 值之間的比率是否為常量的虛擬函數,如果是,則確定該比率的值。|
|[do_in](#do_in)|一個虛擬函數,用於將內部`Byte`值序列轉換為外部`CharType`值序列。|
|[do_length](#do_length)|一個虛擬函數,用於確定`Byte`給定`Byte`外部 值序列中生成不超過給定數量`CharType`的內部值的值的數量並返回該值`Byte`數。|
|[do_max_length](#do_max_length)|虛擬函式，傳回產生一個內部 `CharType` 所需的外部 Byte 數目上限。|
|[do_out](#do_out)|一個虛擬函數,用於將內部`CharType`值序列轉換為外部位元組序列。|
|[do_unshift](#do_unshift)|一個虛擬函數,用於提供`Byte`與狀態相關的轉換中所需的值,以`Byte`完成 值序列中的最後一個字元。|
|[編碼](#encoding)|測試`Byte`流的編碼是否取決於狀態,`Byte`使用的值與生成`CharType`的 值之間的比率是否為常量,如果是,則確定該比率的值。|
|[in](#in)|將`Byte`值序列的外部表示形式轉換`CharType`為 值序列的內部表示形式。|
|[長度](#length)|確定給定外部`Byte``Byte`值序列中產生的值數不超過給定數量的`CharType`內部值,並返回該值數`Byte`。|
|[max_length](#max_length)|返回生成一個內部`Byte``CharType`值所需的最大外部值數。|
|[出](#out)|將內部`CharType`值序列轉換為`Byte`外部 值序列。|
|[unshift](#unshift)|提供與狀態`Byte`相關的轉換中所需的外部值,以完成值序列中的最後`Byte`一 個字元。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="codecvtalways_noconv"></a><a name="always_noconv"></a>編解碼:always_noconv

測試是否需要進行轉換。

```cpp
bool always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

如果不需要執行轉換,則**為 true**的布林值;**假**,如果至少需要做一個。

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

## <a name="codecvtcodecvt"></a><a name="codecvt"></a>編解碼::codecvt

作為地區設定 Facet 處理轉換之 codecvt 類別物件的建構函式。

```cpp
explicit codecvt(size_t refs = 0);
```

### <a name="parameters"></a>參數

*裁判*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- 2: 未定義這些值。

建構函數用區域設定初始化`locale::facet`基本物件[:::面](../standard-library/locale-class.md#facet_class)`(refs)`。

## <a name="codecvtdo_always_noconv"></a><a name="do_always_noconv"></a>編解碼::d_總是_noconv

調用以測試是否需要執行轉換的虛擬函數。

```cpp
virtual bool do_always_noconv() const throw();
```

### <a name="return-value"></a>傳回值

僅當對[do_in](#do_in)或[do_out](#do_out)的每個`noconv`調用返回 時,受保護的虛擬成員函數才會返回**true。**

樣板版本一律會傳回 **true**。

### <a name="example"></a>範例

請參閱呼叫 [always_noconv](#always_noconv) 的範例，其會呼叫 `do_always_noconv`。

## <a name="codecvtdo_encoding"></a><a name="do_encoding"></a>編解碼法::do_編碼

測試`Byte`流的編碼是否取決於狀態、`Byte`使用的值與生成`CharType`的 值之間的比率是否為常量的虛擬函數,如果是,則確定該比率的值。

```cpp
virtual int do_encoding() const throw();
```

### <a name="return-value"></a>傳回值

此受保護的虛擬成員函式會傳回：

- -1,如果類型`extern_type`序列的編碼與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N* (如果編碼只與長度為 *N* 的序列有關)

### <a name="example"></a>範例

請參閱 [encoding](#encoding) 的範例，其會呼叫 `do_encoding`。

## <a name="codecvtdo_in"></a><a name="do_in"></a>編解碼法::do_in

一個虛擬函數,用於將外部`Byte`值序列轉換為內部`CharType`值序列。

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

*第一1*\
要轉換之序列開頭的指標。

*最後1*\
要轉換之序列結尾的指標。

*下一個1*\
超過已轉換序列結尾之第一個未轉換字元的指標。

*第一2*\
已轉換序列開頭的指標。

*最後2*\
已轉換序列結尾的指標。

*下一個2*\
指向`CharType`上次`CharType`轉換 後到達的指標,指向目標序列中第一個未更改的字元。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error`如果源序列格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功。

- `codecvt_base::partial`如果源不足或目標不夠大,則轉換成功。

### <a name="remarks"></a>備註

*狀態*必須表示新源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [in](#in) 的範例，其會呼叫 `do_in`。

## <a name="codecvtdo_length"></a><a name="do_length"></a>編解碼法::do_長度

一個虛擬函數,用於確定`Byte`給定`Byte`外部 值序列中生成不超過給定數量`CharType`的內部值的值的數量並返回該值`Byte`數。

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

*第一1*\
外部序列開頭的指標。

*最後1*\
外部序列結尾的指標。

*len2*\
成員函數可以返回`Byte`的最大值數。

### <a name="return-value"></a>傳回值

表示最大轉換數計數的整數,不大於*len2,* 由`first1`在的外部來源`last1`序列定義 。

### <a name="remarks"></a>備註

受保護的虛擬成員函式有效地呼叫`do_in( state, first1, last1, next1, buf, buf + len2, next2)`*狀態*(狀態的副本)、`buf`一些緩衝區與`next1`指標`next2`和 。

然後傳`next2` - `buf`回 。 因此,它計算的最大轉換數,不大於*len2,* 由源序列`first1``last1`在 * 下定義。

範本版本始終返回最後 1 *first1* - *first1*和*len2*的較小版本。

### <a name="example"></a>範例

請參閱[長度](#length)的範例,該範例`do_length`呼叫 。

## <a name="codecvtdo_max_length"></a><a name="do_max_length"></a>編解碼法::do_max_長度

返回生成內部所需的最大外部`Byte`值數的虛擬函數。 `CharType`

```cpp
virtual int do_max_length() const throw();
```

### <a name="return-value"></a>傳回值

生成一個`CharType`所需的`Byte`最大值數。

### <a name="remarks"></a>備註

受保護的虛擬成員函數傳回do_length對 first1[do_length](#do_length)`( first1, last1, 1)`和*last1*的任意有效值*last1*可以傳回的最大允許值 。

### <a name="example"></a>範例

請參閱 [max_length](#max_length) 的範例，其會呼叫 `do_max_length`。

## <a name="codecvtdo_out"></a><a name="do_out"></a>編解碼法::do_out

一個虛擬函數,用於將內部`CharType`值序列轉換為外部`Byte`值序列。

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

*第一1*\
要轉換之序列開頭的指標。

*最後1*\
要轉換之序列結尾的指標。

*下一個1*\
引用指向第一個未轉換`CharType`的指標,最後一次`CharType`轉換後。

*第一2*\
已轉換序列開頭的指標。

*最後2*\
已轉換序列結尾的指標。

*下一個2*\
引用指向第一個未轉換`Byte`的指標,最後一次`Byte`轉換後。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果源序列格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功。

- `codecvt_base::partial`如果源不足,或者目標不夠大,轉換成功。

### <a name="remarks"></a>備註

*狀態*必須表示新源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 否則不會指定其預存值。

### <a name="example"></a>範例

請參閱 [out](#out) 的範例，其會呼叫 `do_out`。

## <a name="codecvtdo_unshift"></a><a name="do_unshift"></a>編解碼法::do_無移

一個虛擬函數,用於提供`Byte`與狀態相關的轉換中所需的值,以`Byte`完成 值序列中的最後一個字元。

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

*第一2*\
目的範圍中第一個位置的指標。

*最後2*\
目的範圍中最後一個位置的指標。

*下一個2*\
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果*狀態*表示不合法狀態

- `codecvt_base::noconv` (如果函式不會執行任何轉換)

- `codecvt_base::ok`如果轉換成功

- `codecvt_base::partial`如果目標不夠大,無法成功轉換

### <a name="remarks"></a>備註

受保護的虛擬`CharType`成員函數嘗試將源元素 (0) 轉換為它`first2``last2`存儲在 * 中的目標`Byte`序列),終止元素 (0 除外)。 它始終在下*一個 2*中存儲指向目標序列中第一個未更改元素的指標。

_ *State* 必須是新來源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 通常,轉換源元素`CharType`(0) 會使當前狀態處於初始轉換狀態。

### <a name="example"></a>範例

請參閱 [unshift](#unshift) 的範例，其會呼叫 `do_unshift`。

## <a name="codecvtencoding"></a><a name="encoding"></a>編解碼:編碼

測試`Byte`流的編碼是否取決於狀態,`Byte`使用的值與生成`CharType`的 值之間的比率是否為常量,如果是,則確定該比率的值。

```cpp
int encoding() const throw();
```

### <a name="return-value"></a>傳回值

如果返回值為正值,則該值是生成`Byte``CharType`字元所需的字元的恆定數。

此受保護的虛擬成員函式會傳回：

- -1,如果類型`extern_type`序列的編碼與狀態相關。

- 0 (如果編碼與不同長度的序列有關)。

- *N*,如果編碼僅涉及長度*為 N*的序列。

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

## <a name="codecvtextern_type"></a><a name="extern_type"></a>編解碼:extern_type

用於外部表示的字元類型。

```cpp
typedef Byte extern_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `Byte` 的同義字。

## <a name="codecvtin"></a><a name="in"></a>編解碼::在

將`Byte`值序列的外部表示形式轉換`CharType`為 值序列的內部表示形式。

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

*第一1*\
要轉換之序列開頭的指標。

*最後1*\
要轉換之序列結尾的指標。

*下一個1*\
超過已轉換序列結尾之第一個未轉換字元的指標。

*第一2*\
已轉換序列開頭的指標。

*最後2*\
已轉換序列結尾的指標。

*下一個2*\
指標指向`CharType`上次轉換為`Chartype`目標序列中第一個未更改的字元之後的指標。

### <a name="return-value"></a>傳回值

指出作業成功、部分成功或失敗的傳回值。 此函式會傳回：

- `codecvt_base::error`如果源序列格式不正確。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功。

- `codecvt_base::partial`如果源不足,或者目標不夠大,轉換成功。

### <a name="remarks"></a>備註

*狀態*必須表示新源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 部分轉換後,必須設置*狀態*,以便在新字元到達時恢復轉換。

成員函數傳[回 do_in](#do_in)`( state, first1,  last1,  next1, first2, last2,  next2)`。

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

## <a name="codecvtintern_type"></a><a name="intern_type"></a>編解碼:intern_type

用於內部表示的字元類型。

```cpp
typedef CharType intern_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `CharType` 的同義字。

## <a name="codecvtlength"></a><a name="length"></a>編解碼:長度

確定給定外部`Byte``Byte`值序列中產生的值數不超過給定數量的`CharType`內部值,並返回該值數`Byte`。

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

*第一1*\
外部序列開頭的指標。

*最後1*\
外部序列結尾的指標。

*len2*\
可由成員函式傳回的位元組數目上限。

### <a name="return-value"></a>傳回值

表示最大轉換數計數的整數,不大於*len2,* 由`first1`在的外部來源`last1`序列定義 。

### <a name="remarks"></a>備註

成員函數傳回[do_length](#do_length)`( state, first1, last1, len2)`。

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

## <a name="codecvtmax_length"></a><a name="max_length"></a>編解碼:max_length

返回生成一個內部`Byte``CharType`值所需的最大外部值數。

```cpp
int max_length() const throw();
```

### <a name="return-value"></a>傳回值

生成一個`CharType`所需的`Byte`最大值數。

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

## <a name="codecvtout"></a><a name="out"></a>編解碼:出

將內部`CharType`值序列轉換為`Byte`外部 值序列。

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

*第一1*\
要轉換之序列開頭的指標。

*最後1*\
要轉換之序列結尾的指標。

*下一個1*\
引用指向上次`CharType`轉換後第一個`CharType`未 轉換的指標。

*第一2*\
已轉換序列開頭的指標。

*最後2*\
已轉換序列結尾的指標。

*下一個2*\
引用指向上次轉換`Byte``Byte`後第一個未轉換的指標。

### <a name="return-value"></a>傳回值

成員函數傳回[do_out](#do_out)`( state, first1, last1, next1, first2, last2, next2)`。

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

## <a name="codecvtstate_type"></a><a name="state_type"></a>編解碼::state_type

字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。

```cpp
typedef StateType state_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `StateType` 的同義字。

## <a name="codecvtunshift"></a><a name="unshift"></a>編解碼::取消換檔

提供與`Byte`狀態相關的轉換中所需的值,以`Byte`完成 一系列值中的最後一個字元。

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

*第一2*\
目的範圍中第一個位置的指標。

*最後2*\
目的範圍中最後一個位置的指標。

*下一個2*\
目的序列中第一個未變更的元素指標。

### <a name="return-value"></a>傳回值

此函式會傳回：

- `codecvt_base::error`如果狀態表示無效狀態。

- `codecvt_base::noconv` (如果函式不會執行任何轉換)。

- `codecvt_base::ok`如果轉換成功。

- `codecvt_base::partial`如果目標不夠大,無法成功轉換。

### <a name="remarks"></a>備註

受保護的虛擬`CharType`成員函數嘗試將源元素 (0) 轉換為它`first2``last2`存儲在 * 中的目標`Byte`序列),終止元素 (0 除外)。 它始終在下*一個 2*中存儲指向目標序列中第一個未更改元素的指標。

*狀態*必須表示新源序列開頭的初始轉換狀態。 此函式會視需要改變其預存值，以反映成功轉換的目前狀態。 通常,轉換源元素`CharType`(0) 會使當前狀態處於初始轉換狀態。

成員函數[傳回do_unshift](#do_unshift)`( state, first2, last2, next2 )`。

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[代碼頁](../c-runtime-library/code-pages.md)\
[區域設定名稱、語言和國家/區域字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
