---
title: num_get 類別
ms.date: 11/04/2016
f1_keywords:
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
helpviewer_keywords:
- std::num_get [C++]
- std::num_get [C++], char_type
- std::num_get [C++], iter_type
- std::num_get [C++], do_get
- std::num_get [C++], get
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
ms.openlocfilehash: 76d2832141c65ca67c42f1994a3c8f5b532f0092
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373662"
---
# <a name="num_get-class"></a>num_get 類別

描述可用作區域設置面的物件的類範本,用於控制類型`CharType`序列轉換為數值的物件。

## <a name="syntax"></a>語法

```cpp
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>
class num_get : public locale::facet;
```

### <a name="parameters"></a>參數

*字元類型*\
程式內用於編碼地區設定字元的類型。

*輸入反覆運算器*\
數值 get 函式從中讀取其輸入的迭代器類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[num_get](#num_get)|用來從序列擷取數值之 `num_get` 類型物件的建構函式。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|
|[iter_type](#iter_type)|描述輸入迭代器的類型。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_get](#do_get)|虛擬函式，呼叫以從字元序列擷取數值或布林值。|
|[get](#get)|從字元序列擷取數值或布林值。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="num_getchar_type"></a><a name="char_type"></a>num_get:char_type

類型，用來描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型是範本參數 **CharType** 的同義字。

## <a name="num_getdo_get"></a><a name="do_get"></a>num_get::d奧_get

虛擬函式，呼叫以從字元序列擷取數值或布林值。

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

### <a name="parameters"></a>參數

*第一*\
要從中讀取數字的字元範圍開頭。

*最後*\
要從中讀取數字的字元範圍結尾。

*約斯基地*\
旗標供轉換使用的 [ios_base](../standard-library/ios-base-class.md)。

*狀態*\
失敗時會新增 failbit (請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) 的狀態。

*瓦爾*\
已讀取的值。

### <a name="return-value"></a>傳回值

已讀取值之後的迭代器。

### <a name="remarks"></a>備註

第一個虛擬的受保護成員函式

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;
```

匹配序列`[first, last)`中*最初*開始的順序元素,直到它識別出一個完整的非空整數輸入欄位。 如果成功,它將此欄位轉換為其等效值為「**長**」,並將結果存儲在*val*中。 它會傳回迭代器，此迭代器指定數字輸入欄位後的第一個元素。 否則,函數將不儲存*val*val`ios_base::failbit``state`並設置在中。 它會傳回迭代器，此迭代器指定有效整數輸入欄位之任何前置詞後的第一個元素。 不論是上述哪一種情況，如果傳回值等於 `last`，函式就會在 `state` 中設定 `ios_base::eofbit`。

整數輸入欄位由掃描函數用於匹配和轉換檔中一系列**字元**元素的相同規則轉換。 (假定每個此類**字元**元素都通過簡單的一對一映射映射到`Elem`等效 類型的元素。等效掃描轉換規範確定如下:

如果`iosbase.`[ios_base::標記](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[十進位](../standard-library/ios-functions.md#oct),`lo`轉換規範為 。

如果 `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，則轉換規格為 `lx`。

如果 `iosbase.flags() & ios_base::basefield == 0`，則轉換規格為 `li`。

否則，轉換規格會是 `ld`。

整數輸入欄位的格式由呼叫[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.``fac`傳回[的局部區域設置](../standard-library/locale-class.md#facet_class)[:::getloc](../standard-library/ios-base-class.md#getloc) `())` [ios_baseuse_facet](../standard-library/locale-functions.md#use_facet)`<`進一步確定。 具體來說：

`fac.`[numpunct::群組](../standard-library/numpunct-class.md#grouping)`()`確定數位如何群組到任何小數點左側

`fac.`[numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep)`()`確定將數位組分隔到任何小數點左側的序列。

如果沒有任何 `fac.thousands_sep()` 執行個體出現在數字輸入欄位中，就不會施加任何千分號條件約束。 否則，將會強制執行 `fac.grouping()` 所施加的任何千分號條件約束，並在進行掃描轉換之前將分隔符號移除。

第四個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

行為與第一個相同，不同的是，它會以 `lu` 取代 `ld` 轉換規格。 如果成功,它將數字輸入欄位轉換為**未簽署長**類型的值,並將該值儲存在*val*。

第五個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;
```

行為與第一個相同，不同的是，它會以 `lld` 取代 `ld` 轉換規格。 如果成功,它將數字輸入欄位轉換為**長**類型的值,並將該值儲存在*val*。

第六個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;
```

行為與第一個相同，不同的是，它會以 `llu` 取代 `ld` 轉換規格。 如果成功,它將數字輸入欄位轉換為**未簽署長**類型的值,並將該值儲存在*val*。

第七個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;
```

行為與第一個相同，不同的是，它會盡力比對出完整、非空白的浮點數輸入欄位。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()`確定將整數位與分數位數分開的序列。 對等掃描轉換指定名稱是 `lf`。

第八個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

行為與第一個相同，不同的是，它會盡力比對出完整、非空白的浮點數輸入欄位。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()`確定將整數位與分數位數分開的序列。 對等掃描轉換指定名稱是 `lf`。

第九個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

行為與第八個相同，不同的是，對等掃描轉換指定名稱是 `Lf`。

第十個虛擬受保護成員函數:

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

行為與第一個相同，不同的是，對等掃描轉換指定名稱是 `p`。

最後一個 (第十一個) 虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

行為與第一個相同，不同的是，它會盡力比對出完整、非空白的布林值輸入欄位。 如果成功,它將布林輸入欄位轉換為**布林**型態的值,並將該值儲存在*val*。

布林值輸入欄位採用下列兩種形式其中之一。 如果 `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 為 false，它就與整數輸入欄位相同，不同的是，轉換的值必須是 0 (代表 false) 或 1 (代表 true)。 否則,序列必須`fac.`匹配[numpunct::falsename(](../standard-library/numpunct-class.md#falsename)`()`對於 false)或`fac.` [numpunct::truename(](../standard-library/numpunct-class.md#truename)`()`對於 true)。

### <a name="example"></a>範例

請參閱 [get](#get) 的範例，其中會由 `do_get` 呼叫此虛擬成員函式。

## <a name="num_getget"></a><a name="get"></a>num_get:取得

從字元序列擷取數值或布林值。

```cpp
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

### <a name="parameters"></a>參數

*第一*\
要從中讀取數字的字元範圍開頭。

*最後*\
要從中讀取數字的字元範圍結尾。

*約斯基地*\
旗標供轉換使用的 [ios_base](../standard-library/ios-base-class.md)。

*狀態*\
失敗時會新增 failbit (請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) 的狀態。

*瓦爾*\
已讀取的值。

### <a name="return-value"></a>傳回值

已讀取值之後的迭代器。

### <a name="remarks"></a>備註

所有成員函數傳[回 do_get](#do_get)`( first, last, iosbase, state, val)`。

第一個虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的整數輸入欄位為止。 如果成功,它將此欄位轉換為等效值,作為類型**長**並將結果儲存在*val*。 它會傳回迭代器，此迭代器指定數字輸入欄位後的第一個元素。 否則,函數將不儲存*val*val`ios_base::failbit`並設定*狀態*。 它會傳回迭代器，此迭代器指定有效整數輸入欄位之任何前置詞後的第一個元素。 在這兩種情況下,如果返回值等於最後一*個*,則函`ios_base::eofbit`數 將*設定*狀態 。

整數輸入欄位由掃描函數用於匹配和轉換檔中一系列**字元**元素的相同規則轉換。 假定每個此類**字元**元素都通過簡單的一對一映射映射到`CharType`等效 類型的元素。 對等的掃描轉換規格是以下列方式決定：

- 如果`iosbase.`[標誌](../standard-library/ios-base-class.md#flags)`& ios_base::basefield == ios_base::`[為十進位](../standard-library/ios-functions.md#oct)`lo`,則轉換規範為 。

- 如果 `iosbase.flags & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，則轉換規格為 `lx`。

- 如果 `iosbase.flags & ios_base::basefield == 0`，則轉換規格為 `li`。

- 否則，轉換規格會是 `ld`。

整數輸入欄位的格式由調用[use_facet](../standard-library/locale-functions.md#use_facet)`<`[`numpunct`](../standard-library/numpunct-class.md)`<Elem>(iosbase.`[getloc](../standard-library/ios-base-class.md#getloc)`())``fac`返回[的區域設置面](../standard-library/locale-class.md#facet_class)進一步確定。 具體來說：

- `fac.`[分組](../standard-library/numpunct-class.md#grouping)確定數位如何分組到任何小數點左側。

- `fac.`[thousands_sep](../standard-library/numpunct-class.md#thousands_sep)確定將數位組分隔到任何小數點左側的序列。

如果沒有任何 `fac.thousands_sep` 執行個體出現在數字輸入欄位中，就不會施加任何千分號條件約束。 否則,將強制執行施加`fac.grouping`的任何分組約束,並在掃描轉換發生之前刪除分隔符。

第二個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    unsigned long& val) const;
```

行為與第一個相同，不同的是，它會以 `lu` 取代 `ld` 轉換規格。 如果成功,它將數字輸入欄位轉換為**未簽署長**類型的值,並將該值儲存在*val*。

第三個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    double& val) const;
```

行為與第一個相同，不同的是，它會嘗試比對出完整、非空白的浮點數輸入欄位。 `fac.`[decimal_point](../standard-library/numpunct-class.md#decimal_point)確定將整數數位與分數位數分開的序列。 對等掃描轉換指定名稱是 `lf`。

第四個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    long double& val) const;
```

第三個相同的,除了等效的掃描轉換指定器是`Lf`。

第五個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    void *& val) const;
```

行為與第一個相同，不同的是，對等掃描轉換指定名稱是 `p`。

第六個虛擬的受保護成員函式：

```cpp
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& iosbase,
    ios_base::iostate& state,
    bool& val) const;
```

行為與第一個相同，不同的是，它會嘗試比對出完整、非空白的布林值輸入欄位。 如果成功,它將布林輸入欄位轉換為**布林**型態的值,並將該值儲存在*val*。

布林值輸入欄位採用下列兩種形式其中之一。 如果`iosbase.flags & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) **為 false,** 則它與整數輸入欄位相同,只不過轉換的值必須為 0(對於**false)** 或 1(對於**true)。** 否則,序列必須匹配`fac.`[假名](../standard-library/numpunct-class.md#falsename)(**對於 false)** 或`fac.`[真名](../standard-library/numpunct-class.md#truename)(對於**true)。**

### <a name="example"></a>範例

```cpp
// num_get_get.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <sstream>
using namespace std;
int main( )
{
   locale loc( "german_germany" );

   basic_stringstream<char> psz, psz2;
   psz << "-1000,56";

   ios_base::iostate st = 0;
   long double fVal;
   cout << use_facet <numpunct <char> >(loc).thousands_sep( ) << endl;

   psz.imbue( loc );
   use_facet <num_get <char> >
   (loc).get( basic_istream<char>::_Iter( psz.rdbuf( ) ),
           basic_istream<char>::_Iter(0), psz, st, fVal );

   if ( st & ios_base::failbit )
      cout << "money_get( ) FAILED" << endl;
   else
      cout << "money_get( ) = " << fVal << endl;
}
```

## <a name="num_getiter_type"></a><a name="iter_type"></a>num_get:iter_type

描述輸入迭代器的類型。

```cpp
typedef InputIterator iter_type;
```

### <a name="remarks"></a>備註

此類型是樣板參數 `InputIterator` 的同義字。

## <a name="num_getnum_get"></a><a name="num_get"></a>num_get:num_get

用來從序列擷取數值之 `num_get` 類型物件的建構函式。

```cpp
explicit num_get(size_t refs = 0);
```

### <a name="parameters"></a>參數

*裁判*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*refs*參數的可能值及其顯著性為:

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \>1: 未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

構造函數用`locale::`[分面](../standard-library/locale-class.md#facet_class)`(refs)`初始化其基本物件。

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[分面類](../standard-library/locale-class.md#facet_class)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
