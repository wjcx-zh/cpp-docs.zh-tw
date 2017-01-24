---
title: "locale 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocale/std::locale"
  - "std::locale"
  - "std.locale"
  - "locale"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "locale 類別"
ms.assetid: 7dd6d271-472d-4750-8fb5-ea8f55fbef62
caps.latest.revision: 28
caps.handback.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# locale 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述地區設定物件的類別，將特定文化特性資訊封裝做為共同定義特定當地語系化環境的一組 facet。  
  
## <a name="syntax"></a>語法  
  
```  
class locale;  
```  
  
## <a name="remarks"></a>備註  
 Facet 是從類別衍生的類別物件的指標 [facet](#facet_class) 具有格式的 public 物件︰  
  
```  
static locale::id id;  
```  
  
 您可以定義這些 facet 的開放集合。 您也可以建構地區設定物件來指定任意數目的 facet。  
  
 這些 facet 的預先定義的群組代表 [地區設定分類](#locale__category) 傳統上由標準 C 程式庫函式 `setlocale`。  
  
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
  
 類別的地區設定的物件也會儲存地區設定名稱做為類別物件 [字串](../Topic/%3Cstring%3E%20typedefs.md#string)。 使用無效的地區設定名稱來建構地區設定 facet 或地區設定物件類別的物件就會擲回 [runtime_error](../standard-library/runtime-error-class.md)。 如果地區設定物件無法確定 C-Style 地區設定正確對應於物件所表示的項目，儲存的地區設定名稱為 `"*"`。 否則，您可以建立相符的地區設定標準 C 程式庫，地區設定物件內 `_Loc`, ，藉由呼叫 `setlocale`(LC_ALL `,` `_Loc`。 [名稱](#locale__name)`().c_str()`)。  
  
 在這個實作，您也可以呼叫靜態成員函式：  
  
```  
static locale empty();
```  
  
 建構沒有 facet 的地區設定物件。 它也是透明的地區設定;如果樣板函式 [has_facet](../Topic/%3Clocale%3E%20functions.md#has_facet) 和 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) 找不到所要求的 facet 在透明地區設定，這些參考第一次全域地區設定，然後，如果它是透明的傳統的地區設定。 因此，您可以撰寫：  
  
```  
cout.imbue(locale::empty());
```  
  
 後續插入到 [cout](../Topic/%3Ciostream%3E%20functions.md#cout) 由全域地區設定的目前狀態居中協調。 您甚至可以撰寫：  
  
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
|[地區設定](#locale__locale)|建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[類別目錄](#locale__category)|整數類型，提供位元遮罩值以表示標準 facet 系列。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[結合](#locale__combine)|將指定之地區設定的 facet 插入至目標地區設定。|  
|[名稱](#locale__name)|傳回儲存的地區設定名稱。|  
  
### <a name="static-functions"></a>靜態函式  
  
|||  
|-|-|  
|[傳統](#locale__classic)|此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。|  
|[全域](#locale__global)|重設程式的預設地區設定。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[運算子 ！ =](#locale__operator_neq)|測試兩個地區設定是否不等。|  
|[運算子 （)](#locale__operator__)|比較兩個 `basic_string` 物件。|  
|[運算子 = =](#locale__operator_eq_eq)|測試兩個地區設定是否相等。|  
  
### <a name="classes"></a>類別  
  
|||  
|-|-|  
|[facet](#facet_class)|做為所有地區設定 facet 之基底類別的類別。|  
|[識別碼](#id_class)|此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namelocalecategorya-localecategory"></a><a name="locale__category"></a>  locale:: category  
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
 類型是同義字 `int` 可代表一組不同的位元遮罩的項目類型輸入類別的地區設定的本機，或可以用來代表任何對應的 C 地區設定分類。 項目包括︰  
  
- **自動分頁**, ，對應到 C 類別 LC_COLLATE  
  
- **ctype**, ，對應到 C 類別 LC_CTYPE  
  
- **貨幣**, ，對應到 C 類別 LC_MONETARY  
  
- **數值**, ，對應到 C 類別 LC_NUMERIC  
  
- **時間**, ，對應到 C 類別 LC_TIME  
  
- **訊息**, ，對應至 Posix 分類 LC_MESSAGES  
  
 另外，兩個有用的值為︰  
  
- **無**, ，對應到無 C 類別  
  
- **所有**, 、 對應的所有類別 LC_ALL C 等位  
  
 您可以使用代表類別的任意群組 `OR` 完成這些常數，如下所示 **貨幣** &#124; **時間**。  
  
##  <a name="a-namelocaleclassica-localeclassic"></a><a name="locale__classic"></a>  locale:: classic  
 此靜態成員函式傳回表示傳統 C 地區設定的地區設定物件。  
  
```  
static const locale& classic();
```  
  
### <a name="return-value"></a>傳回值  
 對 C 地區設定的參考。  
  
### <a name="remarks"></a>備註  
 傳統 C 地區設定是美國隱含在不國際化的程式中使用標準 C 程式庫內 ASCII 英文地區設定。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namelocalecombinea-localecombine"></a><a name="locale__combine"></a>  locale:: combine  
 將指定之地區設定的 facet 插入至目標地區設定。  
  
```  
template <class Facet>  
locale combine(const locale& _Loc) const;
```  
  
### <a name="parameters"></a>參數  
 `_Loc`  
 包含要插入至目標地區設定 facet 的地區設定。  
  
### <a name="return-value"></a>傳回值  
 成員函式傳回地區設定物件，以取代或加入至 **\*這** facet `Facet` 中列出 `_Loc`。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namefacetclassa-facet-class"></a><a name="facet_class"></a>  facet 類別  
 做為所有地區設定 facet 之基底類別的類別。  
  
facet 類別 {保護︰ 明確 facet (size_t _Refs = 0); 虛擬 ~ facet(); 私用︰ facet(const facet&) / / 未定義 void 運算子 =(const facet&) / / 未定義}。  
  
### <a name="remarks"></a>備註  
 請注意您無法複製或指派類別 facet 的物件。 您可以建立並終結物件衍生自類別 `locale::facet` ，但不是適當的基底類別的物件。 一般而言，您可以建構物件 `_Myfac` 中建構的地區設定時，來自 facet **localeloc**( `locale::classic`（)、 **新**`_Myfac`);  
  
 在這種情況下，基底類別的 facet 建構函式應該有一個零 `_Refs` 引數。 當不再需要物件時，會將其刪除。 因此，您可以提供非零 _ *Refs* 引數只在少數的情況，您負責物件存留期。  
  
##  <a name="a-namelocaleglobala-localeglobal"></a><a name="locale__global"></a>  locale:: global  
 重設程式的預設地區設定。 這會影響到 C 和 c + + 的全域地區設定  
  
```  
static locale global(const locale& _Loc);
```  
  
### <a name="parameters"></a>參數  
 `_Loc`  
 要做為預設的地區設定的程式地區設定。  
  
### <a name="return-value"></a>傳回值  
 先前的地區設定的預設地區設定重設之前。  
  
### <a name="remarks"></a>備註  
 在程式啟動時，全域地區設定是與傳統的地區設定相同。  `global()` 函式呼叫 `setlocale( LC_ALL, loc.name. c_str())` 建立相符的地區設定的標準 C 程式庫中。  
  
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
  
##  <a name="a-nameidclassa-id-class"></a><a name="id_class"></a>  id 類別  
 此成員類別提供唯一 facet 項目識別，做為用於地區設定中查詢 facet 的索引鍵。  
  
類別識別碼 {保護︰ id （）; 私用︰ id(const id&) / / 未定義 void 運算子 =(const id&) / / 未定義}。  
  
### <a name="remarks"></a>備註  
 此成員類別描述所需的每個唯一的地區設定 facet 的靜態成員物件。 請注意，您無法複製或指派的物件類別的 **識別碼**。  
  
##  <a name="a-namelocalelocalea-localelocale"></a><a name="locale__locale"></a>  locale:: locale  
 建立地區設定、地區設定複本，或 facet 或分類已被其他地區設定的 facet 或分類取代的地區設定複本。  
  
```  
locale();

explicit locale(
    const char* _Locname,  
    category _Cat = all);

explicit locale(
    const string& _Locname);

locale(
    const locale& _Loc);

locale(
    const locale& _Loc,   
    const locale& _Other,  
    category _Cat);

locale(
    const locale& _Loc,   
    const char* _Locname,  
    category _Cat);

template <class Facet>  
locale(
 const locale& _Loc,   
    const Facet* _Fac);
```  
  
### <a name="parameters"></a>參數  
 `_Locname`  
 地區設定的名稱。  
  
 `_Loc`  
 複製建構新的地區設定的地區設定。  
  
 `_Other`  
 要從中選取一個類別的地區設定。  
  
 `_Cat`  
 用來取代至建構的地區設定分類。  
  
 `_Fac`  
 用來取代至建構的地區設定 facet。  
  
### <a name="remarks"></a>備註  
 第一個建構函式初始化物件，以符合全域地區設定。 第二個和第三個建構函式初始化具有與地區設定名稱一致的行為的所有地區設定分類 `_Locname`。 其餘的建構函式複製 `_Loc`, ，，例外狀況︰  
  
 `locale(const locale& _Loc, const locale& _Other, category _Cat);`  
  
 取代從 `_Other` 這些 facet 的 c 對應至類別 C （& s) `_Cat` 為非零值。  
  
 `locale(const locale& _Loc, const char* _Locname, category _Cat);`  
  
 `locale(const locale& _Loc, const string& _Locname, category _Cat);`  
  
 取代從 `locale(_Locname, _All)` 這些 facet 的 c 對應至類別 C （& s) `_Cat`為非零值。  
  
 `template<class Facet> locale(const locale& _Loc, Facet* _Fac);`  
  
 取代中 （或加入至） `_Loc` facet `_Fac`, ，如果 `_Fac` 不是 null 指標。  
  
 如果地區設定名稱 `_Locname` 為 null 指標或無效，此函式會擲回 [runtime_error](../standard-library/runtime-error-class.md)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namelocalenamea-localename"></a><a name="locale__name"></a>  locale:: name  
 傳回儲存的地區設定名稱。  
  
```  
string name() const;
```  
  
### <a name="return-value"></a>傳回值  
 字串，指定的地區設定名稱。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namelocaleoperatorneqa-localeoperator"></a><a name="locale__operator_neq"></a>  locale:: operator ！ =  
 測試兩個地區設定是否不等。  
  
```  
bool operator!=(const locale& right) const;
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 要測試不相等的地區設定的其中一個。  
  
### <a name="return-value"></a>傳回值  
 布林值，是 **true** 如果地區設定不相同的地區設定; 的複本 **false** 如果地區設定相同的地區設定的複本。  
  
### <a name="remarks"></a>備註  
 兩個地區設定相等，如果它們是相同的地區設定，如果有另一份，或它們有相同的名稱。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namelocaleoperatora-localeoperator"></a><a name="locale__operator__"></a>  locale:: operator （)  
 比較兩個 `basic_string` 物件。  
  
```  
template <class CharType, class Traits, class Allocator>  
bool operator()(
    const basic_string<CharType, Traits, Allocator>& left,  
    const basic_string<CharType, Traits, Allocator>& right) const;
```  
  
### <a name="parameters"></a>參數  
 ` left`  
 左邊的字串。  
  
 ` right`  
 右邊的字串。  
  
### <a name="return-value"></a>傳回值  
 成員函式會傳回︰  
  
-   如果小於第二個序列比較的第一個序列的-1。  
  
-   如果第二個序列比較的第一個序列小於 + 1。  
  
-   0，表示序列相等。  
  
### <a name="remarks"></a>備註  
 成員函式有效地執行︰  
  
```  
const collate<CharType>& fac = use_fac<collate<CharType>>(*this);

return (fac.compare(left.begin(), left.end(), right.begin(), right.end()) <0);
```  
  
 因此，您可以使用的地區設定物件為函式物件。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namelocaleoperatoreqeqa-localeoperator"></a><a name="locale__operator_eq_eq"></a>  locale:: operator = =  
 測試兩個地區設定是否相等。  
  
```  
bool operator==(const locale& right) const;
```  
  
### <a name="parameters"></a>參數  
 ` right`  
 若要測試相等的地區設定的其中一個。  
  
### <a name="return-value"></a>傳回值  
 布林值，是 **true** 如果地區設定相同的地區設定; 的複本 **false** 如果地區設定不相同的地區設定的複本。  
  
### <a name="remarks"></a>備註  
 兩個地區設定相等，如果它們是相同的地區設定，如果有另一份，或它們有相同的名稱。  
  
### <a name="example"></a>範例  
  
```  
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
 [\< 地區設定>](../standard-library/locale.md)   
 [字碼頁](../c-runtime-library/code-pages.md)   
 [地區設定名稱、 語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

