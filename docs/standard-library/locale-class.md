---
title: locale 類別
ms.date: 03/19/2019
f1_keywords:
- xlocale/std::locale
- xlocale/std::locale::category
- xlocale/std::locale::combine
- xlocale/std::locale::name
- xlocale/std::locale::classic
- xlocale/std::locale::global
- xlocale/std::locale::operator( )
- xlocale/std::locale::facet
- xlocale/std::locale::id
helpviewer_keywords:
- std::locale [C++]
- std::locale [C++], category
- std::locale [C++], combine
- std::locale [C++], name
- std::locale [C++], classic
- std::locale [C++], global
- std::locale [C++], facet
- std::locale [C++], id
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
ms.openlocfilehash: 2581c5cdacc9e542f5d911860128dcf5526621ef
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/14/2020
ms.locfileid: "81367308"
---
# <a name="locale-class"></a>locale 類別

描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。

## <a name="syntax"></a>語法

```cpp
class locale;
```

## <a name="remarks"></a>備註

facet 是一個指標，指向 [facet](#facet_class) 類別所衍生類別的物件，具有以下形式的公用物件：

```cpp
static locale::id id;
```

您可以定義這些 facet 的開放集合。 您也可以建構地區設定物件來指定任意數目的 facet。

這些 facet 的預先定義群組代表在「標準 C 程式庫」中傳統上由 `setlocale` 函式管理的[地區設定分類](#category)。

類別`collate`(LC_COLLATE)包括以下幾個方面:

```cpp
collate<char>
collate<wchar_t>
```

類別`ctype`(LC_CTYPE)包括以下幾個方面:

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

類別`monetary`(LC_MONETARY)包括以下幾個方面:

```cpp
moneypunct<char, false>
moneypunct<wchar_t, false>
moneypunct<char, true>
moneypunct<wchar_t, true>
money_get<char, istreambuf_iterator<char>>
money_get<wchar_t, istreambuf_iterator<wchar_t>>
money_put<char, ostreambuf_iterator<char>>
money_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

類別`numeric`(LC_NUMERIC)包括以下幾個方面:

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

類別`time`(LC_TIME)包括以下幾個方面:

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

類別`messages`(LC_MESSAGES)包括以下幾個方面:

```cpp
messages<char>
messages<wchar_t>
```

(最後一個類別由 POSIX 要求,但不是 C 標準要求。

`iostream`類使用其中一些預定義的分面來控制數值在文本序列的轉換。

locale 類別的物件也會將地區設定名稱儲存為 [string](../standard-library/string-typedefs.md#string) 類別的物件。 使用無效的地區設定名稱來建構地區設定 facet 或地區設定物件時，會擲回 [runtime_error](../standard-library/runtime-error-class.md) 類別的物件。 儲存區域設定名稱是`"*"`,如果區域設置物件無法確定 C 樣式區域設置是否與物件表示的區域設置完全對應。 `locale_object`否則,可以通過調`setlocale(LC_ALL , locale_object.`用[name](#name)`().c_str())`在標準 C 庫中為某些區域設置物件建立匹配區域設置。

在這個實作，您也可以呼叫靜態成員函式：

```cpp
static locale empty();
```

建構沒有 facet 的地區設定物件。 這也是一個透明的區域設置。 如果樣本[has_facet](../standard-library/locale-functions.md#has_facet)功能,[並且use_facet](../standard-library/locale-functions.md#use_facet)在透明區域設置中找不到請求的分面,則他們首先諮詢全域區域設置,然後,如果它是透明的,則先諮詢經典區域設置。 因此,您可以編寫:

```cpp
cout.imbue(locale::empty());
```

後續插入[`cout`](../standard-library/iostream.md#cout)由全域區域設置的當前狀態進行仲介。 您甚至可以撰寫：

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

即使全域地區設定提供插入日期和貨幣金額數量的變更規則，對 `cout` 後續插入的數字格式化規則與 C 地區設定保持相同。

### <a name="constructors"></a>建構函式

|建構函式|描述|
|-|-|
|[現場](#locale)|建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|描述|
|-|-|
|[類別](#category)|整數類型，提供位元遮罩值以表示標準 facet 系列。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[結合](#combine)|將指定之地區設定的 facet 插入至目標地區設定。|
|[名稱](#name)|傳回儲存的地區設定名稱。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[經典](#classic)|此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。|
|[全球](#global)|重設程式的預設地區設定。|

### <a name="operators"></a>操作員

|運算子|描述|
|-|-|
|[運算子*](#op_eq)|分配區域設置。|
|[操作員!](#op_neq)|測試兩個地區設定是否不等。|
|[操作員( )](#op_call)|比較兩個 `basic_string` 物件。|
|[運算子*](#op_eq_eq)|測試兩個地區設定是否相等。|

### <a name="classes"></a>類別

|類別|描述|
|-|-|
|[方面](#facet_class)|做為所有地區設定 facet 之基底類別的類別。|
|[`id`](#id_class)|此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。|

## <a name="requirements"></a>需求

**標頭︰** \<locale>

**命名空間：** std

## <a name="localecategory"></a><a name="category"></a>區域設定:類別

整數類型，提供位元遮罩值以表示標準 facet 系列。

```cpp
typedef int category;
static const int collate = LC_COLLATE;
static const int ctype = LC_CTYPE;
static const int monetary = LC_MONETARY;
static const int numeric = LC_NUMERIC;
static const int time = LC_TIME;
static const int messages = LC_MESSAGES;
static const int all = LC_ALL;
static const int none = 0;
```

### <a name="remarks"></a>備註

該類型是**int**類型的同義詞,可以表示位掩碼類型到類區域設置的一組不同元素,或者可用於表示任何相應的 C 區域設置類別。 這些元素如下：

- `collate`,對應於 C 類別LC_COLLATE

- `ctype`,對應於 C 類別LC_CTYPE

- `monetary`,對應於 C 類別LC_MONETARY

- `numeric`,對應於 C 類LC_NUMERIC

- `time`,對應於 C 類LC_TIME

- `messages`,對應於 POSIX 類別LC_MESSAGES

兩個更有用的值是:

- `none`,對應於任何 C 類別

- `all`,對應於所有類別的 C 聯合LC_ALL

可以使用這些常量表示任意類別`OR`組,如`monetary`&#124; `time`。

## <a name="localeclassic"></a><a name="classic"></a>區域設置::經典

此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。

```cpp
static const locale& classic();
```

### <a name="return-value"></a>傳回值

對 C 地區設定的參考。

### <a name="remarks"></a>備註

經典的 C 區域設置是標準 C 庫中的美國英語 ASCII 區域設置。 它是未國際化的程式中隱式使用區域設置。

### <a name="example"></a>範例

```cpp
// locale_classic.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: " << loc2.name( )
        << "." << endl;
   cout << "The name of the current locale is: " << loc1.name( )
        << "." << endl;

   if (loc2 == locale::classic( ) )
      cout << "The previous locale was classic." << endl;
   else
      cout << "The previous locale was not classic." << endl;

   if (loc1 == locale::classic( ) )
      cout << "The current locale is classic." << endl;
   else
      cout << "The current locale is not classic." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
The previous locale was classic.
The current locale is not classic.
```

## <a name="localecombine"></a><a name="combine"></a>區域設定::合併

將指定之地區設定的 facet 插入至目標地區設定。

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>參數

*source_locale*\
包含要插入到目標地區設定中之 facet 的地區設定。

### <a name="return-value"></a>傳回值

成員函數傳回區域設定物件,該物件取代 source_locale`Facet`*中列出的*分面或**\*將加入此 。**

### <a name="example"></a>範例

```cpp
// locale_combine.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main() {
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s; it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   locale loc2 ( "C" );
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   locale loc3 = loc2.combine<collate<_TCHAR> > (loc);
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;
}
```

## <a name="facet-class"></a><a name="facet_class"></a>分面類

做為所有地區設定 facet 之基底類別的類別。

```cpp
class facet {
protected:
    explicit facet(size_t references = 0);
    virtual ~facet();
private:
    facet(const facet&) // not defined
    void operator=(const facet&) // not defined
};
```

### <a name="remarks"></a>備註

不能複製或分配類`facet`的物件。 您可以建構和終結衍生自 `locale::facet` 類別的物件，但這不適用於基底類別的物件。 通常,構造從構造`_Myfac``facet``locale`時派生的物件,如`locale loc(locale::classic(), new _Myfac);`

在這種情況下,基類`facet`的構造函數應具有零*引用*參數。 當不再需要該物件時,它被刪除,因此僅在對物件的存留期負責的極少數情況下提供非零*引用*參數。

## <a name="localeglobal"></a><a name="global"></a>區域設定::全球

重設程式的預設地區設定。 此調用會影響 C 和 C++的全域區域設置。

```cpp
static locale global(const locale& new_default_locale);
```

### <a name="parameters"></a>參數

*new_default_locale*\
程式要用來作為預設地區設定的地區設定。

### <a name="return-value"></a>傳回值

重設預設地區設定前的上一個地區設定。

### <a name="remarks"></a>備註

在程式啟動時，全域地區設定會與傳統地區設定相同。 `global()` 函式會呼叫 `setlocale( LC_ALL, loc.name. c_str())` 以在「標準 C 程式庫」中建立相符的地區設定。

### <a name="example"></a>範例

```cpp
// locale_global.cpp
// compile by using: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( )
{
   locale loc ( "German_germany" );
   locale loc1;
   cout << "The initial locale is: " << loc1.name( ) << endl;
   locale loc2 = locale::global ( loc );
   locale loc3;
   cout << "The current locale is: " << loc3.name( ) << endl;
   cout << "The previous locale was: " << loc2.name( ) << endl;
}
```

```Output
The initial locale is: C
The current locale is: German_Germany.1252
The previous locale was: C
```

## <a name="id-class"></a><a name="id_class"></a>id 類別

此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。

```cpp
class id
{
   protected:    id();
   private:      id(const id&)
   void operator=(const id&)  // not defined
};
```

### <a name="remarks"></a>備註

此成員類別描述每個唯一的地區設定 facet 所需的靜態成員物件。 不能複製或分配類`id`的物件。

## <a name="localelocale"></a><a name="locale"></a>區域設定:區域設定

建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。 還包括析構函數。

```cpp
locale();

explicit locale(const char* locale_name, category new_category = all);
explicit locale(const string& locale_name);
locale(const locale& from_locale);
locale(const locale& from_locale, const locale& Other, category new_category);
locale(const locale& from_locale, const char* locale_name, category new_category);

template <class Facet>
locale(const locale& from_locale, const Facet* new_facet);

~locale();
```

### <a name="parameters"></a>參數

*locale_name*\
地區設定的名稱。

*from_locale*\
在建構新地區設定時所要複製的地區設定。

*其他*\
要從中選取分類的地區設定。

*new_category*\
要代入到所建構之地區設定中的分類。

*new_facet*\
要代入到所建構之地區設定中的 facet。

### <a name="remarks"></a>備註

第一個建構函式會將物件初始化以符合全域地區設定。 第二個和第三個構造函數初始化所有區域設置類別,使其行為與區域設置名稱*locale_name*一致。 其餘建構函數複製*from_locale,* 但另有說明的例外情況:

`locale(const locale& from_locale, const locale& Other, category new_category);`

從與 C 類對應*的其他*方面替換 C *&new_category*為非零。

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

從`locale(locale_name, all)`與非零的類別*replace_category*`replace_category & new_category`對應的方面替換。

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

如果*new_facet*不是空*指標,則*替換(或添加到 *)from_locale*分new_facet。

若區域設定名稱*locale_name*為空指標或其他無效,則[函數將runtime_error](../standard-library/runtime-error-class.md)引發 。

### <a name="example"></a>範例

```cpp
// locale_locale.cpp
// compile with: /EHsc
#include <locale>
#include <iostream>
#include <tchar.h>
using namespace std;

int main( ) {

   // Second constructor
   locale loc ( "German_germany" );
   _TCHAR * s1 = _T("Das ist wei\x00dfzz."); // \x00df is the German sharp-s, it comes before z in the German alphabet
   _TCHAR * s2 = _T("Das ist weizzz.");
   int result1 = use_facet<collate<_TCHAR> > ( loc ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc ) << result1 << endl;

   // The first (default) constructor
   locale loc2;
   int result2 = use_facet<collate<_TCHAR> > ( loc2 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc2 )  << result2 << endl;

   // Third constructor
   locale loc3 (loc2,loc, _M_COLLATE );
   int result3 = use_facet<collate<_TCHAR> > ( loc3 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc3 ) << result3 << endl;

   // Fourth constructor
   locale loc4 (loc2, "German_Germany", _M_COLLATE );
   int result4 = use_facet<collate<_TCHAR> > ( loc4 ).
      compare (s1, &s1[_tcslen( s1 )-1 ],  s2, &s2[_tcslen( s2 )-1 ] );
   cout << isalpha (_T ( '\x00df' ), loc4 ) << result4 << endl;
}
```

## <a name="localename"></a><a name="name"></a>區域設定::名稱

傳回儲存的地區設定名稱。

```cpp
string name() const;
```

### <a name="return-value"></a>傳回值

提供地區設定名稱的字串。

### <a name="example"></a>範例

```cpp
// locale_name.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "german" );
   locale loc2 = locale::global( loc1 );
   cout << "The name of the previous locale is: "
        << loc2.name( ) << "." << endl;
   cout << "The name of the current locale is: "
        << loc1.name( ) << "." << endl;
}
```

```Output
The name of the previous locale is: C.
The name of the current locale is: German_Germany.1252.
```

## <a name="localeoperator"></a><a name="op_eq"></a>區域設定::操作員*

分配區域設置。

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>區域設置::操作員!*

測試兩個地區設定是否不等。

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>參數

*對*\
其中一個要測試是否不相等的地區設定。

### <a name="return-value"></a>傳回值

如果區域設置不是同一區域設置的副本,則**布爾值為 true。** 如果區域設置是同一區域設置的副本,則**為 false。**

### <a name="remarks"></a>備註

如果兩個區域設置是相同的區域設置,如果區域設置是另一個區域設置的副本,或者它們具有相同的名稱,則兩個區域設置相等。

### <a name="example"></a>範例

```cpp
// locale_op_ne.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 != loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc2 (" << loc2.name( ) << ") are equal." << endl;

   if ( loc1 != loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are not equal." << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ") and\n loc3 (" << loc3.name( ) << ") are equal." << endl;
}
```

```Output
locales loc1 (German_Germany.1252) and
loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252) and
loc3 (English_United States.1252) are not equal.
```

## <a name="localeoperator"></a><a name="op_call"></a>區域設置::操作員()

比較兩個 `basic_string` 物件。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>參數

*離開*\
左字串。

*對*\
右字串。

### <a name="return-value"></a>傳回值

成員函式會傳回：

- –1，表示第一個序列比第二個序列小。

- +1，表示第二個序列比第一個序列小。

- 0，表示序列相等。

### <a name="remarks"></a>備註

成員函式會實際執行：

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

這意味著您可以將區域設置物件用作函數物件。

### <a name="example"></a>範例

```cpp
// locale_op_compare.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

int main( )
{
   using namespace std;
   wchar_t *sa = L"ztesting";
   wchar_t *sb = L"\0x00DFtesting";
   basic_string<wchar_t> a( sa );
   basic_string<wchar_t> b( sb );

   locale loc( "German_Germany" );
   cout << loc( a,b ) << endl;

   const collate<wchar_t>& fac = use_facet<collate<wchar_t> >( loc );
   cout << ( fac.compare( sa, sa + a.length( ),
       sb, sb + b.length( ) ) < 0) << endl;
}
```

```Output
0
0
```

## <a name="localeoperator"></a><a name="op_eq_eq"></a>區域設定::操作員*

測試兩個地區設定是否相等。

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>參數

*對*\
其中一個要測試是否相等的地區設定。

### <a name="return-value"></a>傳回值

如果區域設置是同一區域設置的副本,則**布爾值為 true。** 如果區域設置不是同一區域設置的副本,則**為 false。**

### <a name="remarks"></a>備註

如果兩個區域設置是相同的區域設置,如果區域設置是另一個區域設置的副本,或者它們具有相同的名稱,則兩個區域設置相等。

### <a name="example"></a>範例

```cpp
// locale_op_eq.cpp
// compile with: /EHsc
#include <iostream>
#include <string>
#include <locale>

using namespace std;

int main( )
{
   locale loc1( "German_Germany" );
   locale loc2( "German_Germany" );
   locale loc3( "English" );

   if ( loc1 == loc2 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc2 (" << loc2.name( ) << ") are not equal."
      << endl;

   if ( loc1 == loc3 )
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are equal."
      << endl;
   else
      cout << "locales loc1 (" << loc1.name( )
      << ")\n and loc3 (" << loc3.name( ) << ") are not equal."
      << endl;
}
```

```Output
locales loc1 (German_Germany.1252)
and loc2 (German_Germany.1252) are equal.
locales loc1 (German_Germany.1252)
and loc3 (English_United States.1252) are not equal.
```

## <a name="see-also"></a>另請參閱

[\<區域設定>](../standard-library/locale.md)\
[代碼頁](../c-runtime-library/code-pages.md)\
[區域設定名稱、語言和國家/區域字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
