---
title: locale 類別
ms.date: 07/20/2020
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
ms.openlocfilehash: 771a2973e0254194d99ddfd46ca7df7d6cc8e5a4
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224821"
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

Category `collate` （LC_COLLATE）包含 facet：

```cpp
collate<char>
collate<wchar_t>
```

Category `ctype` （LC_CTYPE）包含 facet：

```cpp
ctype<char>
ctype<wchar_t>
codecvt<char, char, mbstate_t>
codecvt<wchar_t, char, mbstate_t>
codecvt<char16_t, char, mbstate_t>
codecvt<char32_t, char, mbstate_t>
```

Category `monetary` （LC_MONETARY）包含 facet：

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

Category `numeric` （LC_NUMERIC）包含 facet：

```cpp
num_get<char, istreambuf_iterator<char>>
num_get<wchar_t, istreambuf_iterator<wchar_t>>
num_put<char, ostreambuf_iterator<char>>
num_put<wchar_t, ostreambuf_iterator<wchar_t>>
numpunct<char>
numpunct<wchar_t>
```

Category `time` （LC_TIME）包含 facet：

```cpp
time_get<char, istreambuf_iterator<char>>
time_get<wchar_t, istreambuf_iterator<wchar_t>>
time_put<char, ostreambuf_iterator<char>>
time_put<wchar_t, ostreambuf_iterator<wchar_t>>
```

Category `messages` （LC_MESSAGES）包含 facet：

```cpp
messages<char>
messages<wchar_t>
```

（最後一個分類是 POSIX 所需，但不是 C 標準）。

這些類別會使用其中一些預先定義的 facet `iostream` ，以控制將數值轉換成文字序列的方式，以及從文字順序轉換。

locale 類別的物件也會將地區設定名稱儲存為 [string](../standard-library/string-typedefs.md#string) 類別的物件。 使用無效的地區設定名稱來建構地區設定 facet 或地區設定物件時，會擲回 [runtime_error](../standard-library/runtime-error-class.md) 類別的物件。 儲存的地區設定名稱是指 `"*"` 地區設定物件無法確定 C 樣式地區設定是否完全對應至物件所代表的地區設定。 否則，您可以藉 `locale_object` 由呼叫 `setlocale(LC_ALL , locale_object.` [名稱](#name)，在標準 C 程式庫中建立符合的地區設定 `().c_str())` 。

在這個實作，您也可以呼叫靜態成員函式：

```cpp
static locale empty();
```

建構沒有 facet 的地區設定物件。 它也是透明的地區設定。 如果範本函式[has_facet](../standard-library/locale-functions.md#has_facet) ，且[use_facet](../standard-library/locale-functions.md#use_facet)在透明地區設定中找不到要求的 facet，則會先查閱全域地區設定，如果是透明的，則是傳統的地區設定。 因此，您可以撰寫：

```cpp
cout.imbue(locale::empty());
```

的後續插入 [`cout`](../standard-library/iostream.md#cout) 是由全域地區設定的目前狀態所 mediated。 您甚至可以撰寫：

```cpp
locale loc(locale::empty(),
    locale::classic(),
    locale::numeric);

cout.imbue(loc);
```

即使全域地區設定提供插入日期和貨幣金額數量的變更規則，對 `cout` 後續插入的數字格式化規則與 C 地區設定保持相同。

### <a name="constructors"></a>建構函式

|建構函式|說明|
|-|-|
|[locale](#locale)|建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。|

### <a name="typedefs"></a>Typedefs

|類型名稱|說明|
|-|-|
|[類別](#category)|整數類型，提供位元遮罩值以表示標準 facet 系列。|

### <a name="member-functions"></a>成員函數

|成員函數|描述|
|-|-|
|[起來](#combine)|將指定之地區設定的 facet 插入至目標地區設定。|
|[name](#name)|傳回儲存的地區設定名稱。|

### <a name="static-functions"></a>靜態函式

|||
|-|-|
|[傳統](#classic)|此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。|
|[全域性](#global)|重設程式的預設地區設定。|

### <a name="operators"></a>操作員

|運算子|說明|
|-|-|
|[operator =](#op_eq)|指派地區設定。|
|[operator！ =](#op_neq)|測試兩個地區設定是否不等。|
|[operator （）](#op_call)|比較兩個 `basic_string` 物件。|
|[operator = =](#op_eq_eq)|測試兩個地區設定是否相等。|

### <a name="classes"></a>類別

|類別|說明|
|-|-|
|[facet](#facet_class)|做為所有地區設定 facet 之基底類別的類別。|
|[`id`](#id_class)|此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。|

## <a name="requirements"></a>需求

**標頭：**\<locale>

**命名空間：** std

## <a name="localecategory"></a><a name="category"></a>locale：： category

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

類型是類型的同義字 **`int`** ，可以代表類別地區設定區域之位元遮罩類型的相異元素群組，或可用來表示任何對應的 C 地區設定分類。 這些元素如下：

- `collate`，對應至 C 類別目錄 LC_COLLATE

- `ctype`，對應至 C 類別目錄 LC_CTYPE

- `monetary`，對應至 C 類別目錄 LC_MONETARY

- `numeric`，對應至 C 類別目錄 LC_NUMERIC

- `time`，對應至 C 類別目錄 LC_TIME

- `messages`，對應至 POSIX 類別目錄 LC_MESSAGES

另外兩個有用的值如下：

- `none`，對應于 C 類別目錄以外的所有

- `all`，對應至所有分類的 C 聯集 LC_ALL

您可以使用與這些常數來表示任意類別群組 `OR` ，如同 `monetary` &#124; `time` 。

## <a name="localeclassic"></a><a name="classic"></a>locale：：傳統

此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。

```cpp
static const locale& classic();
```

### <a name="return-value"></a>傳回值

對 C 地區設定的參考。

### <a name="remarks"></a>備註

傳統 C 地區設定是標準 C 程式庫中的美國英文 ASCII 地區設定。 這是在不會國際化的程式中隱含使用的地區設定。

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

## <a name="localecombine"></a><a name="combine"></a>locale：：組合

將指定之地區設定的 facet 插入至目標地區設定。

```cpp
template <class Facet>
locale combine(const locale& source_locale) const;
```

### <a name="parameters"></a>參數

*source_locale*\
包含要插入到目標地區設定中之 facet 的地區設定。

### <a name="return-value"></a>傳回值

此成員函式會傳回地區設定物件，以取代中的，或**將其加入至 \* ** `Facet` *source_locale*中列出的 facet。

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

## <a name="facet-class"></a><a name="facet_class"></a>facet 類別

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

您無法複製或指派類別的物件 `facet` 。 您可以建構和終結衍生自 `locale::facet` 類別的物件，但這不適用於基底類別的物件。 一般而言， `_Myfac` 當您建立時，您會建立衍生自的物件 `facet` `locale` ，如下所示：`locale loc(locale::classic(), new _Myfac);`

在這種情況下，基類的函式 `facet` 應該有零個*參考*引數。 當不再需要物件時，會將它刪除，因此您只會在那些罕見的情況下，提供非零的*參考*引數給您負責物件的存留期。

## <a name="localeglobal"></a><a name="global"></a>locale：： global

重設程式的預設地區設定。 此呼叫會影響 C 和 c + + 的全域地區設定。

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

此成員類別描述每個唯一的地區設定 facet 所需的靜態成員物件。 您無法複製或指派類別的物件 `id` 。

## <a name="localelocale"></a><a name="locale"></a>locale：： locale

建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。 也包含一個析構函式。

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

*另一方面*\
要從中選取分類的地區設定。

*new_category*\
要代入到所建構之地區設定中的分類。

*new_facet*\
要代入到所建構之地區設定中的 facet。

### <a name="remarks"></a>備註

第一個建構函式會將物件初始化以符合全域地區設定。 第二個和第三個函式會初始化所有地區設定分類，使其行為與地區設定名稱*locale_name*一致。 其餘的函式會複製*from_locale*，並注明例外狀況：

`locale(const locale& from_locale, const locale& Other, category new_category);`

取代*其他*與 C & *new_category*為非零的類別 c 對應的 facet。

`locale(const locale& from_locale, const char* locale_name, category new_category);`

`locale(const locale& from_locale, const string& locale_name, category new_category);`

取代 `locale(locale_name, all)` 對應于分類*replace_category*的 facet，其 `replace_category & new_category` 為非零值。

`template<class Facet> locale(const locale& from_locale, Facet* new_facet);`

如果*new_facet*不是 null 指標，則會在 facet *new_facet*中取代（或將加入至） *from_locale* 。

如果地區設定名稱*locale_name*是 null 指標或無效，則函數會擲回[runtime_error](../standard-library/runtime-error-class.md)。

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

## <a name="localename"></a><a name="name"></a>locale：： name

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

## <a name="localeoperator"></a><a name="op_eq"></a>locale：： operator =

指派地區設定。

```cpp
const locale& operator=(const locale& other) noexcept;
```

## <a name="localeoperator"></a><a name="op_neq"></a>locale：： operator！ =

測試兩個地區設定是否不等。

```cpp
bool operator!=(const locale& right) const;
```

### <a name="parameters"></a>參數

*再*\
其中一個要測試是否不相等的地區設定。

### <a name="return-value"></a>傳回值

布林值， **`true`** 如果地區設定不是相同地區設定的複本，則為。 這是因為 **`false`** 地區設定是相同地區設定的複本。

### <a name="remarks"></a>備註

如果兩個地區設定是相同的地區設定，則為，如果其中一個是另一個的複本，則為，如果它們有相同的名稱，則為。

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

## <a name="localeoperator"></a><a name="op_call"></a>locale：： operator （）

`basic_string`根據這個地區設定的 std：： collate facet 所定義的詞典編纂比較規則，比較兩個物件 <charT> 。

```cpp
template <class CharType, class Traits, class Allocator>
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,
    const basic_string<CharType, Traits, Allocator>& right) const;
```

### <a name="parameters"></a>參數

*左面*\
要比較的第一個字串。

*再*\
要比較的第二個字串。

### <a name="return-value"></a>傳回值

- **`true`** 如果*left*的詞典編纂小於*right*，則為，否則為 **`false`** 。

### <a name="remarks"></a>備註

成員函式會實際執行：

```cpp
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```

這表示您可以使用地區設定物件做為函式物件。

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
   const wchar_t *sa = L"ztesting";
   const wchar_t *sb = L"\0x00DFtesting";
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

## <a name="localeoperator"></a><a name="op_eq_eq"></a>locale：： operator = =

測試兩個地區設定是否相等。

```cpp
bool operator==(const locale& right) const;
```

### <a name="parameters"></a>參數

*再*\
其中一個要測試是否相等的地區設定。

### <a name="return-value"></a>傳回值

布林值， **`true`** 如果地區設定是相同地區設定的複本，則為。 這是因為 **`false`** 地區設定不是相同地區設定的複本。

### <a name="remarks"></a>備註

如果兩個地區設定是相同的地區設定，則為，如果其中一個是另一個的複本，則為，如果它們有相同的名稱，則為。

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

[\<locale>](../standard-library/locale.md)\
[字碼頁](../c-runtime-library/code-pages.md)\
[地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)
