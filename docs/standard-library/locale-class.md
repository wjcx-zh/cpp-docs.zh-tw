---
title: "locale 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocale/std::locale
- locale
- locale/std::locale::category
- locale/std::locale::combine
- locale/std::locale::name
- locale/std::locale::classic
- locale/std::locale::global
- locale/std::locale::operator( )
- locale/std::locale::facet
- locale/std::locale::id
dev_langs:
- C++
helpviewer_keywords:
- locale class
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
caps.latest.revision: 28
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Machine Translation
ms.sourcegitcommit: 66798adc96121837b4ac2dd238b9887d3c5b7eef
ms.openlocfilehash: 6e33e125d2689d37443bec58c5b01f5b7e72ccfd
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="locale-class"></a>locale 類別
描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。  
  
## <a name="syntax"></a>語法  
  
```  
class locale;  
```  
  
## <a name="remarks"></a>備註  
 facet 是一個指標，指向 [facet](#facet_class) 類別所衍生類別的物件，具有以下形式的公用物件：  
  
```  
static locale::id id;  
```  
  
 您可以定義這些 facet 的開放集合。 您也可以建構地區設定物件來指定任意數目的 facet。  
  
 這些 facet 的預先定義群組代表在「標準 C 程式庫」中傳統上由 `setlocale` 函式管理的[地區設定分類](#category)。  
  
 分類 collate (LC_COLLATE) 包含下列 facet：  
  
```  
collate<char>  
collate<wchar_t>  
```  
  
 分類 ctype (LC_CTYPE) 包含下列 facet：  
  
```  
ctype<char>  
ctype<wchar_t>  
codecvt<char, char, mbstate_t>  
codecvt<wchar_t, char, mbstate_t>  
codecvt<char16_t, char, mbstate_t>  
codecvt<char32_t, char, mbstate_t>  
```  
  
 分類 monetary (LC_MONETARY) 包含下列 facet：  
  
```  
moneypunct<char, false>  
moneypunct<wchar_t, false>  
moneypunct<char, true>  
moneypunct<wchar_t, true>  
money_get<char, istreambuf_iterator<char>>  
money_get<wchar_t, istreambuf_iterator<wchar_t>>  
money_put<char, ostreambuf_iterator<char>>  
money_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 分類 numeric (LC_NUMERIC) 包含下列 facet：  
  
```  
num_get<char, istreambuf_iterator<char>>  
num_get<wchar_t, istreambuf_iterator<wchar_t>>  
num_put<char, ostreambuf_iterator<char>>  
num_put<wchar_t, ostreambuf_iterator<wchar_t>>  
numpunct<char>  
numpunct<wchar_t>  
```  
  
 分類 time (LC_TIME) 包含下列 facet：  
  
```  
time_get<char, istreambuf_iterator<char>>  
time_get<wchar_t, istreambuf_iterator<wchar_t>>  
time_put<char, ostreambuf_iterator<char>>  
time_put<wchar_t, ostreambuf_iterator<wchar_t>>  
```  
  
 分類 messages (LC_MESSAGES) 包含下列 facet：  
  
```  
messages<char>  
messages<wchar_t>  
```  
  
 (最後分類為 Posix 所需，但 C Standard 不需要。)  
  
 iostreams 類別使用某些預先定義的 facet，以控制數值轉換和文字序列之間來回轉換。  
  
 locale 類別的物件也會將地區設定名稱儲存為 [string](../standard-library/string-typedefs.md#string) 類別的物件。 使用無效的地區設定名稱來建構地區設定 facet 或地區設定物件時，會擲回 [runtime_error](../standard-library/runtime-error-class.md) 類別的物件。 如果地區設定物件無法確定 C-Style 地區設定正確對應於物件所表示的項目，儲存的地區設定名稱為 `"*"`。 否則，您可以在「標準 C 程式庫」內，針對地區設定物件 `Loc`，建立相符的地區設定，方法是呼叫 `setlocale`(LC_ALL `,` `Loc`. [name](#name)`().c_str()`)。  
  
 在這個實作，您也可以呼叫靜態成員函式：  
  
```  
static locale empty();
```  
  
 建構沒有 facet 的地區設定物件。 它也是一個透明地區設定；如果範本函式 [has_facet](../standard-library/locale-functions.md#has_facet) 和 [use_facet](../standard-library/locale-functions.md#use_facet) 在透明地區設定中找不到所要求的 facet，就會先查閱全域地區設定，然後，如果該地區設定是透明的，就再查閱傳統地區設定。 因此，您可以撰寫：  
  
```  
cout.imbue(locale::empty());
```  
  
後續對 [cout](../standard-library/iostream.md#cout) 的插入是由全域地區設定的目前狀態所調解。 您甚至可以撰寫：  
  
```  
locale loc(locale::empty(),
    locale::classic(),  
    locale::numeric);

cout.imbue(loc);
```   
  
 即使全域地區設定提供插入日期和貨幣金額數量的變更規則，對 `cout` 後續插入的數字格式化規則與 C 地區設定保持相同。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[locale](#locale)|建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[category](#category)|整數類型，提供位元遮罩值以表示標準 facet 系列。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[combine](#combine)|將指定之地區設定的 facet 插入至目標地區設定。|  
|[name](#name)|傳回儲存的地區設定名稱。|  
  
### <a name="static-functions"></a>靜態函式  
  
|||  
|-|-|  
|[classic](#classic)|此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。|  
|[global](#global)|重設程式的預設地區設定。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator!=](#op_neq)|測試兩個地區設定是否不等。|  
|[operator( )](#op_call)|比較兩個 `basic_string` 物件。|  
|[operator==](#op_eq_eq)|測試兩個地區設定是否相等。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[facet](#facet_class)|做為所有地區設定 facet 之基底類別的類別。|  
|[id](#id_class)|此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="category"></a>  locale::category  
 整數類型，提供位元遮罩值以表示標準 facet 系列。  
  
```  
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
 此類型與 `int` 類型同義，int 類型可代表 locale 類別本機位元遮罩類型的一組不同元素，或可用來代表任何對應的 C locale 類別。 這些元素如下：  
  
- **collate**：與 C 分類 LC_COLLATE 對應  
  
- **ctype**：與 C 分類 LC_CTYPE 對應  
  
- **monetary**：與 C 分類 LC_MONETARY 對應  
  
- **numeric**：與 C 分類 LC_NUMERIC 對應  
  
- **time**：與 C 分類 LC_TIME 對應  
  
- **messages**：與 Posix 分類 LC_MESSAGES 對應  
  
 此外，兩個有用的值如下：  
  
- **none**：與任何 C 分類都不對應  
  
- **all**：與 C 所有分類 LC_ALL 的聯集對應  
  
 您可以像在 **monetary** &#124; **time** 中一樣，使用 `OR` 搭配這些常數來代表任意的分類群組。  
  
##  <a name="classic"></a>  locale::classic  
 此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。  
  
```  
static const locale& classic();
```  
  
### <a name="return-value"></a>傳回值  
 對 C 地區設定的參考。  
  
### <a name="remarks"></a>備註  
 傳統 C 地區設定是「標準 C 程式庫」內的美式英文 ASCII 地區設定，這是未國際化的程式中以隱含方式使用的地區設定。  
  
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
  
##  <a name="combine"></a>  locale::combine  
 將指定之地區設定的 facet 插入至目標地區設定。  
  
```  
template <class Facet>  
locale combine(const locale& Loc) const;
```  
  
### <a name="parameters"></a>參數  
 `Loc`  
 包含要插入到目標地區設定中之 facet 的地區設定。  
  
### <a name="return-value"></a>傳回值  
 此成員函式會傳回地區設定物件，此物件會在 **\*this** 中取代或新增 `Loc` 中所列的 facet `Facet`。  
  
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
  
##  <a name="facet_class"></a>  facet 類別  
 做為所有地區設定 facet 之基底類別的類別。  

```    
class facet { 
protected:    
    explicit facet(size_t _Refs = 0);
   virtual ~facet();
private:    
   facet(const facet&)
   // not defined void operator=(const facet&)
     // not defined    
};  
```  
### <a name="remarks"></a>備註  
 請注意，您無法複製或指派 facet 類別的物件。 您可以建構和終結衍生自 `locale::facet` 類別的物件，但這不適用於基底類別的物件。 一般而言，您會在建構地區設定時，建構衍生自 facet 的物件 `_Myfac`，就像在 **localeloc**( `locale::classic`( ), **new**`_Myfac`); 中一樣  
  
 在這類情況下，基底類別 facet 的建構函式應該有一個為零的 `_Refs` 引數。 當不再需要該物件時，系統就會將它刪除。 因此，只有在您需要負責物件存留期的罕見情況下，您才需要提供一個不為零的 _ *Refs* 引數。  
  
##  <a name="global"></a>  locale::global  
 重設程式的預設地區設定。 這會同時影響 C 和 C++ 的全域地區設定。  
  
```  
static locale global(const locale& Loc);
```  
  
### <a name="parameters"></a>參數  
 `Loc`  
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
  
##  <a name="id_class"></a>  id 類別  
 此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。  
  
class id { protected:    id(); private:    id(const id&) // not defined void operator=(const id&)  // not defined    };  
  
### <a name="remarks"></a>備註  
 此成員類別描述每個唯一的地區設定 facet 所需的靜態成員物件。 請注意，您無法複製或指派 **id** 類別的物件。  
  
##  <a name="locale"></a>  locale::locale  
 建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。  
  
```  
locale();

explicit locale(const char* Locname, category Cat = all);
explicit locale(const string& Locname);
locale( const locale& Loc);
locale(const locale& Loc, const locale& Other, category Cat);
locale(const locale& Loc, const char* Locname, category Cat);

template <class Facet>  
locale(const locale& Loc, const Facet* Fac);
```  
  
### <a name="parameters"></a>參數  
 `Locname`  
 地區設定的名稱。  
  
 `Loc`  
 在建構新地區設定時所要複製的地區設定。  
  
 `Other`  
 要從中選取分類的地區設定。  
  
 `Cat`  
 要代入到所建構之地區設定中的分類。  
  
 `Fac`  
 要代入到所建構之地區設定中的 facet。  
  
### <a name="remarks"></a>備註  
 第一個建構函式會將物件初始化以符合全域地區設定。 第二個和第三個建構函式會將所有地區設定類別初始化，以地區設定名稱 `Locname` 讓行為保持一致。 其餘的建構函式會複製 `Loc`，但需注意下列例外：  
  
 `locale(const locale& Loc, const locale& Other, category Cat);`  
  
 會從 `Other` 取代與 C & `Cat` 不為零之分類 C 對應的 facet。  
  
 `locale(const locale& Loc, const char* Locname, category Cat);`  
  
 `locale(const locale& Loc, const string& Locname, category Cat);`  
  
 會從 `locale(Locname, _All)` 取代與 C & `Cat` 不為零之分類 C 對應的 facet。  
  
 `template<class Facet> locale(const locale& Loc, Facet* Fac);`  
  
 如果 `Fac` 不是 Null 指標，就會在 `Loc` 中取代 (或新增) facet `Fac`。  
  
 如果地區設定名稱 `Locname` 是 Null 指標或無效，函式就會擲回 [runtime_error](../standard-library/runtime-error-class.md)。  
  
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
  
##  <a name="name"></a>  locale::name  
 傳回儲存的地區設定名稱。  
  
```  
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
  
##  <a name="op_neq"></a>  locale::operator!=  
 測試兩個地區設定是否不等。  
  
```  
bool operator!=(const locale& right) const;
```  
  
### <a name="parameters"></a>參數  
 `right`  
 其中一個要測試是否不相等的地區設定。  
  
### <a name="return-value"></a>傳回值  
 如果地區設定不是相同地區設定的複本，便會傳回 **true** 布林值；如果地區設定是相同地區設定的複本，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 兩個地區設定如果是相同的地區設定、如果其中一個是另一個的複本，或如果具有相同的名稱，兩者便相等。  
  
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
  
##  <a name="op_call"></a>  locale::operator()  
 比較兩個 `basic_string` 物件。  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right) const;
```  
  
### <a name="parameters"></a>參數  
 `left`  
 左字串。  
  
 `right`  
 右字串。  
  
### <a name="return-value"></a>傳回值  
 成員函式會傳回下列值：  
  
-   –1，表示第一個序列比第二個序列小。  
  
-   +1，表示第二個序列比第一個序列小。  
  
-   0，表示序列相等。  
  
### <a name="remarks"></a>備註  
 成員函式會實際執行：  
  
```  
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) < 0);
```  
  
 因此，您可以使用地區設定物件作為函式物件。  
  
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
  
##  <a name="op_eq_eq"></a>  locale::operator==  
 測試兩個地區設定是否相等。  
  
```  
bool operator==(const locale& right) const;
```  
  
### <a name="parameters"></a>參數  
 `right`  
 其中一個要測試是否相等的地區設定。  
  
### <a name="return-value"></a>傳回值  
 如果地區設定是相同地區設定的複本，便會傳回 **true** 布林值；如果地區設定不是相同地區設定的複本，則會傳回 **false**。  
  
### <a name="remarks"></a>備註  
 兩個地區設定如果是相同的地區設定、如果其中一個是另一個的複本，或如果具有相同的名稱，兩者便相等。  
  
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
 [<locale>](../standard-library/locale.md)   
 [字碼頁](../c-runtime-library/code-pages.md)   
 [地區設定名稱、語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


