---
title: ctype 類別
ms.date: 11/04/2016
f1_keywords:
- xlocale/std::ctype
- xlocale/std::ctype::char_type
- xlocale/std::ctype::do_is
- xlocale/std::ctype::do_narrow
- xlocale/std::ctype::do_scan_is
- xlocale/std::ctype::do_scan_not
- xlocale/std::ctype::do_tolower
- xlocale/std::ctype::do_toupper
- xlocale/std::ctype::do_widen
- xlocale/std::ctype::is
- xlocale/std::ctype::narrow
- xlocale/std::ctype::scan_is
- xlocale/std::ctype::scan_not
- xlocale/std::ctype::tolower
- xlocale/std::ctype::toupper
- xlocale/std::ctype::widen
helpviewer_keywords:
- std::ctype [C++]
- std::ctype [C++], char_type
- std::ctype [C++], do_is
- std::ctype [C++], do_narrow
- std::ctype [C++], do_scan_is
- std::ctype [C++], do_scan_not
- std::ctype [C++], do_tolower
- std::ctype [C++], do_toupper
- std::ctype [C++], do_widen
- std::ctype [C++], is
- std::ctype [C++], narrow
- std::ctype [C++], scan_is
- std::ctype [C++], scan_not
- std::ctype [C++], tolower
- std::ctype [C++], toupper
- std::ctype [C++], widen
ms.assetid: 3627154c-49d9-47b5-b28f-5bbedee38e3b
ms.openlocfilehash: 640b2cc8506e498006feedbea6825a0e51a88209
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421888"
---
# <a name="ctype-class"></a>ctype 類別

類別，提供用於字元分類、大小寫轉換，以及原生字元集和地區設定所用字元集之間轉換的 facet。

## <a name="syntax"></a>語法

```cpp
template <class CharType>
class ctype : public ctype_base;
```

### <a name="parameters"></a>參數

*CharType*\
用於程式內部字元編碼的類型。

## <a name="remarks"></a>備註

如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取其預存值時，會在 `id` 中儲存唯一的正值。 基底類別 ctype_base 中為分類準則提供巢狀位元遮罩類型。

C++標準程式庫會定義此類別範本的兩個明確特製化：

- `ctype<char>`，會分別描述其差異的明確特製化。 如需詳細資訊，請參閱[ctype&lt;char&gt; 類別](../standard-library/ctype-char-class.md)。

- `ctype<wchar_t>`，會將元素視為寬字元。

類別樣板的其他特製化 `ctype<CharType>`：

- 將*CharType*類型的值*ch*轉換成**char**類型的值，並將 expression `(char)ch`。

- 使用運算式 `CharType(byte)`，將**char**類型的值*Byte*轉換為*CharType*類型的值。

所有其他作業都會以與明確特製化 `ctype<char>`相同的方式，在**char**值上執行。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[ctype](#ctype)|`ctype` 類別物件的建構函式，這些物件做為字元的地區設定 facet。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[char_type](#char_type)|類型，描述由地區設定使用的字元。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[do_is](#do_is)|虛擬函式，呼叫以測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。|
|[do_narrow](#do_narrow)|虛擬函式，呼叫以將地區設定所使用之 `CharType` 類型的字元，轉換為原生字元集中**char**類型的對應字元。|
|[do_scan_is](#do_scan_is)|虛擬函式，呼叫以尋找範圍中符合指定之遮罩的第一個字元。|
|[do_scan_not](#do_scan_not)|虛擬函式，呼叫以尋找範圍中不符合指定之遮罩的第一個字元。|
|[do_tolower](#do_tolower)|虛擬函式，呼叫以將字元或字元範圍轉換為小寫。|
|[do_toupper](#do_toupper)|虛擬函式，呼叫以將字元或字元範圍轉換為大寫。|
|[do_widen](#do_widen)|虛擬函式，呼叫以將原生字元集中**char**類型的字元轉換為地區設定所使用 `CharType` 類型的對應字元。|
|[is](#is)|測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。|
|[narrow](#narrow)|將地區設定使用的 `CharType` 類型的字元轉換為原生字元集中 char 類型的對應字元。|
|[scan_is](#scan_is)|尋找範圍中符合指定之遮罩的第一個字元。|
|[scan_not](#scan_not)|尋找範圍中不符合指定之遮罩的第一個字元。|
|[tolower](#tolower)|將字元或字元範圍轉換為小寫。|
|[toupper](#toupper)|將字元或字元範圍轉換為大寫。|
|[widen](#widen)|將原生字元集中類型為**char**的字元，轉換為地區設定所使用 `CharType` 類型的對應字元。|

## <a name="requirements"></a>需求

**標頭：** \<地區設定 >

**命名空間:** std

## <a name="char_type"></a>  ctype::char_type

類型，描述由地區設定使用的字元。

```cpp
typedef CharType char_type;
```

### <a name="remarks"></a>備註

此類型與樣板參數 *CharType* 同義。

### <a name="example"></a>範例

請參閱成員函式 [widen](#widen) 的範例，其會使用 `char_type` 作為傳回值。

## <a name="ctype"></a>  ctype::ctype

ctype 類別物件的建構函式，可作為字元的地區設定 Facet。

```cpp
explicit ctype(size_t _Refs = 0);
```

### <a name="parameters"></a>參數

*_Refs*\
整數值，用來指定物件的記憶體管理類型。

### <a name="remarks"></a>備註

*_Refs*參數和其重要性的可能值為：

- 0：物件的存留期由包含該物件的地區設定來管理。

- 1：物件的存留期必須以手動方式管理。

- \> 1：未定義這些值。

無法提供任何直接範例，因為解構函式受到保護。

建構函式會以 `locale::facet`locale::facet[( ](../standard-library/locale-class.md#facet_class)) 初始化其 `_Refs` 基底物件。

## <a name="do_is"></a>  ctype::do_is

虛擬函式，呼叫以測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。

```cpp
virtual bool do_is(
    mask maskVal,
    CharType ch) const;

virtual const CharType *do_is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>參數

*maskVal*\
要為其測試字元的遮罩值。

*ch*\
要測試其屬性的字元。

*第一個*\
要分類其屬性的範圍中，第一個字元的指標。

*上次*\
要分類其屬性的範圍中，緊接著最後一個字元的指標。

*目的地*\
陣列的開頭指標，其中遮罩值會說明每個字元所要儲存之屬性的特性。

### <a name="return-value"></a>傳回值

如果測試的字元具有遮罩值所描述的屬性，第一個成員函式會傳回 **true** 的布林值；如果字元不具有該屬性，則為 **false**。

第二個成員函式會傳回陣列，其中包含的遮罩值說明範圍中每個字元之屬性的特性。

### <a name="remarks"></a>備註

[ctype_base](../standard-library/ctype-base-class.md) 類別 (其為 ctype 衍生來源) 會提供遮罩值，來分類字元的屬性。 第一個成員函式可以接受第一個參數的運算式，該參數稱為位元遮罩，由邏輯位元運算子 (&#124;、&、^、~) 透過遮罩值組合構成。

### <a name="example"></a>範例

請參閱 [is](#is) 的範例，其會呼叫 `do_is`。

## <a name="do_narrow"></a>  ctype::do_narrow

虛擬函式，呼叫以將地區設定所使用之 `CharType` 類型的字元，轉換為原生字元集中**char**類型的對應字元。

```cpp
virtual char do_narrow(
    CharType ch,
    char default = '\0') const;

virtual const CharType* do_narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>參數

*ch*\
地區設定所用並要進行轉換的 `Chartype` 類型字元。

*預設*\
成員函式指派給不具有類型**char**之對應字元之 `CharType` 類型字元的預設值。

*第一個*\
要轉換的字元範圍中，第一個字元的指標。

*上次*\
要轉換的字元範圍中，緊接著最後一個字元的指標。

*目的地*\
儲存已轉換字元範圍之目的範圍中， **char**類型第一個字元的常數指標。

### <a name="return-value"></a>傳回值

第一個受保護的成員函式會傳回 char 類型的原生字元，其對應于類型 `CharType` 或*預設值*（如果未定義對應的參數字元）。

第二個受保護的成員函式會傳回原生字元 (從 `CharType` 類型字元轉換而來) 目的範圍的指標。

### <a name="remarks"></a>備註

第二個受保護的成員範本函式會針對間隔 [0，`I``default``I`）中的 `last`，儲存在 `dest`[`I`] 值 `do_narrow`（`first` [ - ]，`first`）。

### <a name="example"></a>範例

請參閱 [narrow](#narrow) 的範例，其會呼叫 `do_narrow`。

## <a name="do_scan_is"></a>  ctype::do_scan_is

虛擬函式，呼叫以尋找範圍中符合指定之遮罩的第一個字元。

```cpp
virtual const CharType *do_scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*maskVal*\
字元要比對的遮罩值。

*第一個*\
要掃描的範圍中，第一個字元的指標。

*上次*\
要掃描的範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

範圍中，符合指定遮罩之第一個字元的指標。 如果沒有這類值，函數會傳回*last*。

### <a name="remarks"></a>備註

Protected 成員函式會傳回[do_is](#do_is)（`maskVal`，\* `ptr`）為 true 的範圍 [`first`，`last`）中的最小指標 `ptr`。

### <a name="example"></a>範例

請參閱 [scan_is](#scan_is) 的範例，其會呼叫 `do_scan_is`。

## <a name="do_scan_not"></a>  ctype::do_scan_not

虛擬函式，呼叫以尋找範圍中不符合指定之遮罩的第一個字元。

```cpp
virtual const CharType *do_scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*maskVal*\
字元不會比對的遮罩值。

*第一個*\
要掃描的範圍中，第一個字元的指標。

*上次*\
要掃描的範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

範圍中，不符合指定遮罩之第一個字元的指標。 如果沒有這類值，函數會傳回*last*。

### <a name="remarks"></a>備註

Protected 成員函式會傳回[do_is](#do_is)（`maskVal`，\* `ptr`）為 false 之範圍 [`first`，`last`）中的最小指標 `ptr`。

### <a name="example"></a>範例

請參閱 [scan_not](#scan_not) 的範例，其會呼叫 `do_scan_not`。

## <a name="do_tolower"></a>  ctype::do_tolower

要將字元或字元範圍轉換為小寫時所呼叫的虛擬函式。

```cpp
virtual CharType do_tolower(CharType ch) const;

virtual const CharType *do_tolower(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換為小寫的字元。

*第一個*\
要轉換大小寫的字元範圍中，第一個字元的指標。

*上次*\
要轉換大小寫的字元範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

第一個受保護的成員函式會傳回參數*ch*的小寫形式。 如果沒有小寫形式存在，則會傳回*ch*。 第二個受保護的成員函式會傳回*last*。

### <a name="remarks"></a>備註

第二個受保護的成員範本函式會以  - （`first`[`do_tolower`]）取代間隔 [0，`last``first` `I`）中的每個元素 `first` [`I`] `I`。

### <a name="example"></a>範例

請參閱 [tolower](#tolower) 的範例，其會呼叫 `do_tolower`。

## <a name="do_toupper"></a>  ctype::do_toupper

虛擬函式，呼叫以將字元或字元範圍轉換為大寫。

```cpp
virtual CharType do_toupper(CharType ch) const;

virtual const CharType *do_toupper(
    CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換為大寫的字元。

*第一個*\
要轉換大小寫的字元範圍中，第一個字元的指標。

*上次*\
要轉換大小寫的字元範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

第一個受保護的成員函式會傳回參數*ch*的大寫形式。 如果沒有大寫形式存在，則會傳回*ch*。 第二個受保護的成員函式會傳回*last*。

### <a name="remarks"></a>備註

第二個受保護的成員範本函式會以  - （`first`[`do_toupper`]）取代間隔 [0，`last``first` `I`）中的每個元素 `first` [`I`] `I`。

### <a name="example"></a>範例

請參閱 [toupper](#toupper) 的範例，其會呼叫 `do_toupper`。

## <a name="do_widen"></a>  ctype::do_widen

虛擬函式，呼叫以將原生字元集中**char**類型的字元轉換為地區設定所使用 `CharType` 類型的對應字元。

```cpp
virtual CharType do_widen(char byte) const;

virtual const char *do_widen(
    const char* first,
    const char* last,
    CharType* dest) const;
```

### <a name="parameters"></a>參數

*byte*\
要轉換的原生字元集中， **char**類型的字元。

*第一個*\
要轉換的字元範圍中，第一個字元的指標。

*上次*\
要轉換的字元範圍中，緊接著最後一個字元的指標。

*目的地*\
在目的範圍 (其會儲存轉換的字元範圍) 中，第一個 `CharType` 類型字元的指標。

### <a name="return-value"></a>傳回值

第一個受保護的成員函式會傳回對應于原生類型**char**之參數字元 `CharType` 類型的字元。

第二個受保護的成員函式會傳回類型字元的目的地範圍指標，`CharType` 由從**char**類型的原生字元轉換而來的地區設定所使用。

### <a name="remarks"></a>備註

第二個受保護的成員範本函式會在 `dest`[ `I`] 中儲存 `do_widen` 的值 `first`( `I`[ `I`])，間隔為 [0, `last` - `first`)。

### <a name="example"></a>範例

請參閱 [widen](#widen) 的範例，其會呼叫 `do_widen`。

## <a name="is"></a>  ctype::is

測試單一字元是否有特定屬性，或分類範圍中每個字元的屬性並將其儲存在陣列中。

```cpp
bool is(mask maskVal, CharType ch) const;

const CharType *is(
    const CharType* first,
    const CharType* last,
    mask* dest) const;
```

### <a name="parameters"></a>參數

*maskVal*\
要為其測試字元的遮罩值。

*ch*\
要測試其屬性的字元。

*第一個*\
要分類其屬性的範圍中，第一個字元的指標。

*上次*\
要分類其屬性的範圍中，緊接著最後一個字元的指標。

*目的地*\
陣列的開頭指標，其中遮罩值會說明每個字元所要儲存之屬性的特性。

### <a name="return-value"></a>傳回值

如果測試的字元具有遮罩值所描述的屬性，則第一個成員函式會傳回**true** ;如果無法擁有屬性，則**為 false** 。

第二個成員函式會傳回要分類其屬性的範圍中，最後一個字元的指標。

### <a name="remarks"></a>備註

[ctype_base](../standard-library/ctype-base-class.md) 類別 (其為 ctype 衍生來源) 會提供遮罩值，來分類字元的屬性。 第一個成員函式可以接受第一個參數的運算式，該參數稱為位元遮罩，由邏輯位元運算子 (&#124;、&、^、~) 透過遮罩值組合構成。

### <a name="example"></a>範例

```cpp
// ctype_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main() {
   locale loc1 ( "German_Germany" ), loc2 ( "English_Australia" );

   if (use_facet<ctype<char> > ( loc1 ).is( ctype_base::alpha, 'a' ))
      cout << "The character 'a' in locale loc1 is alphabetic."
           << endl;
   else
      cout << "The character 'a' in locale loc1 is not alphabetic."
           << endl;

   if (use_facet<ctype<char> > ( loc2 ).is( ctype_base::alpha, '!' ))
      cout << "The character '!' in locale loc2 is alphabetic."
           << endl;
   else
      cout << "The character '!' in locale loc2 is not alphabetic."
           << endl;

   char *string = "Hello, my name is John!";
   ctype<char>::mask maskarray[30];
   use_facet<ctype<char> > ( loc2 ).is(
      string, string + strlen(string), maskarray );
   for (unsigned int i = 0; i < strlen(string); i++) {
      cout << string[i] << ": "
           << (maskarray[i] & ctype_base::alpha  "alpha"
                                                : "not alpha")
           << endl;;
   };
}
```

## <a name="narrow"></a>  ctype::narrow

將地區設定使用之 `CharType` 類型的字元，轉換為原生字元集中**char**類型的對應字元。

```cpp
char narrow(CharType ch, char default = '\0') const;

const CharType* narrow(
    const CharType* first,
    const CharType* last,
    char default,
    char* dest) const;
```

### <a name="parameters"></a>參數

*ch*\
地區設定所用並要進行轉換的 `Chartype` 類型字元。

*預設*\
成員函式指派給不具有類型**char**之對應字元之 `CharType` 類型字元的預設值。

*第一個*\
要轉換的字元範圍中，第一個字元的指標。

*上次*\
要轉換的字元範圍中，緊接著最後一個字元的指標。

*目的地*\
儲存已轉換字元範圍之目的範圍中， **char**類型第一個字元的常數指標。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回**char**類型的原生字元，其對應至類型 `CharType default` 的參數字元，如果未定義對應項則為。

第二個成員函式會傳回原生字元 (從 `CharType` 類型字元轉換而來) 目的範圍的指標。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_narrow](#do_narrow)（`ch`，`default`）。 第二個成員函式會傳回[do_narrow](#do_narrow) （`first`、`last`、`default`、`dest`）。 只有基本來源字元的 `CharType` 下方保證會有唯一的反向影像 `narrow`。 針對這些基本來源字元，下列非變異值會保留：`narrow` ( [widen](#widen) ( **c** ), 0 ) == **c**。

### <a name="example"></a>範例

```cpp
// ctype_narrow.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "english" );
   wchar_t *str1 = L"\x0392fhello everyone";
   char str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).narrow
      ( str1, str1 + wcslen(str1), 'X', &str2[0] ) != 0);  // C4996
   str2[wcslen(str1)] = '\0';
   wcout << str1 << endl;
   cout << &str2[0] << endl;
}
```

```Output
Xhello everyone
```

## <a name="scan_is"></a>  ctype::scan_is

尋找範圍中符合指定之遮罩的第一個字元。

```cpp
const CharType *scan_is(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*maskVal*\
字元要比對的遮罩值。

*第一個*\
要掃描的範圍中，第一個字元的指標。

*上次*\
要掃描的範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

範圍中，符合指定遮罩之第一個字元的指標。 如果沒有這類值，函數會傳回*last*。

### <a name="remarks"></a>備註

此成員函式會傳回[do_scan_is](#do_scan_is)（`maskVal`，`first`，`last`）。

### <a name="example"></a>範例

```cpp
// ctype_scan_is.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_is
      ( ctype_base::punct, string, string + strlen(string) );
   cout << "The first punctuation is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
The first punctuation is "," at position: 5
```

## <a name="scan_not"></a>  ctype::scan_not

尋找範圍中不符合指定之遮罩的第一個字元。

```cpp
const CharType *scan_not(
    mask maskVal,
    const CharType* first,
    const CharType* last) const;
```

### <a name="parameters"></a>參數

*maskVal*\
字元不會比對的遮罩值。

*第一個*\
要掃描的範圍中，第一個字元的指標。

*上次*\
要掃描的範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

範圍中，不符合指定遮罩之第一個字元的指標。 如果沒有這類值，函數會傳回*last*。

### <a name="remarks"></a>備註

此成員函式會傳回[do_scan_not](#do_scan_not)（`maskVal`，`first`，`last`）。

### <a name="example"></a>範例

```cpp
// ctype_scan_not.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char *string = "Hello, my name is John!";

   const char* i = use_facet<ctype<char> > ( loc1 ).scan_not
      ( ctype_base::alpha, string, string + strlen(string) );
   cout << "First nonalpha character is \"" << *i << "\" at position: "
      << i - string << endl;
}
```

```Output
First nonalpha character is "," at position: 5
```

## <a name="tolower"></a>  ctype::tolower

將字元或字元範圍轉換為小寫。

```cpp
CharType tolower(CharType ch) const;

const CharType *tolower(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換為小寫的字元。

*第一個*\
要轉換大小寫的字元範圍中，第一個字元的指標。

*上次*\
要轉換大小寫的字元範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回參數*ch*的小寫形式。 如果沒有小寫形式存在，則會傳回*ch*。

第二個成員函式會傳回*last*。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_tolower](#do_tolower)（`ch`）。 第二個成員函式會傳回[do_tolower](#do_tolower)（`first`，`last`）。

### <a name="example"></a>範例

```cpp
// ctype_tolower.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "HELLO, MY NAME IS JOHN";

   use_facet<ctype<char> > ( loc1 ).tolower
      ( string, string + strlen(string) );
   cout << "The lowercase string is: " << string << endl;
}
```

```Output
The lowercase string is: hello, my name is john
```

## <a name="toupper"></a>  ctype::toupper

將字元或字元範圍轉換為大寫。

```cpp
CharType toupper(CharType ch) const;
const CharType *toupper(CharType* first, const CharType* last) const;
```

### <a name="parameters"></a>參數

*ch*\
要轉換為大寫的字元。

*第一個*\
要轉換大小寫的字元範圍中，第一個字元的指標。

*上次*\
要轉換大小寫的字元範圍中，緊接著最後一個字元的指標。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回參數*ch*的大寫形式。 如果沒有大寫形式存在，則會傳回*ch*。

第二個成員函式會傳回*last*。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_toupper](#do_toupper)（`ch`）。 第二個成員函式會傳回 [do_toupper](#do_toupper)( `first`, `last`)。

### <a name="example"></a>範例

```cpp
// ctype_toupper.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "German_Germany" );

   char string[] = "Hello, my name is John";

   use_facet<ctype<char> > ( loc1 ).toupper
      ( string, string + strlen(string) );
   cout << "The uppercase string is: " << string << endl;
}
```

```Output
The uppercase string is: HELLO, MY NAME IS JOHN
```

## <a name="widen"></a>  ctype::widen

將原生字元集中類型為**char**的字元，轉換為地區設定所使用 `CharType` 類型的對應字元。

```cpp
CharType widen(char byte) const;
const char *widen(const char* first, const char* last, CharType* dest) const;
```

### <a name="parameters"></a>參數

*byte*\
原生字元集中要轉換的 char 類型字元。

*第一個*\
要轉換的字元範圍中，第一個字元的指標。

*上次*\
要轉換的字元範圍中，緊接著最後一個字元的指標。

*目的地*\
在目的範圍 (其會儲存轉換的字元範圍) 中，第一個 `CharType` 類型字元的指標。

### <a name="return-value"></a>傳回值

第一個成員函式會傳回對應于原生類型**char**之參數字元 `CharType` 類型的字元。

第二個成員函式會將指標傳回至類型的字元目的範圍，`CharType` 由從**char**類型的原生字元轉換的地區設定所使用。

### <a name="remarks"></a>備註

第一個成員函式會傳回[do_widen](#do_widen)（`byte`）。 第二個成員函式會傳回[do_widen](#do_widen)（`first`，`last`，`dest`）。

### <a name="example"></a>範例

```cpp
// ctype_widen.cpp
// compile with: /EHsc /W3
#include <locale>
#include <iostream>
using namespace std;

int main( )
{
   locale loc1 ( "English" );
   char *str1 = "Hello everyone!";
   wchar_t str2 [16];
   bool result1 = (use_facet<ctype<wchar_t> > ( loc1 ).widen
      ( str1, str1 + strlen(str1), &str2[0] ) != 0);  // C4996
   str2[strlen(str1)] = '\0';
   cout << str1 << endl;
   wcout << &str2[0] << endl;

   ctype<wchar_t>::char_type charT;
   charT = use_facet<ctype<char> > ( loc1 ).widen( 'a' );
}
```

```Output
Hello everyone!
Hello everyone!
```

## <a name="see-also"></a>另請參閱

[\<locale>](../standard-library/locale.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
