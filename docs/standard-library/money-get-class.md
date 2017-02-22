---
title: "money_get 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "xlocmon/std::money_get"
  - "money_get"
  - "std.money_get"
  - "std::money_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_get 類別"
ms.assetid: 692d3374-3fe7-4b46-8aeb-f8d91ed66b2e
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# money_get 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以控制類型 `CharType` 的序列轉換為貨幣值。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class money_get : public locale::facet;
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
 `InputIterator`  
 get 函式從中讀取其輸入的迭代器類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼。**  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[money_get](#money_get__money_get)|`money_get` 類型物件的建構函式，用來從表示貨幣值的序列擷取數值。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_get__char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#money_get__iter_type)|描述輸入迭代器的類型。|  
|[string_type](#money_get__string_type)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_get](#money_get__do_get)|虛擬函式，呼叫以從代表貨幣值的字元序列擷取數值。|  
|[取得](#money_get__get)|從代表貨幣值的字元序列擷取數值。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namemoneygetchartypea-moneygetchartype"></a><a name="money_get__char_type"></a>  money_get:: char_type  
 類型，用來描述由地區設定使用的字元。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType**。  
  
##  <a name="a-namemoneygetdogeta-moneygetdoget"></a><a name="money_get__do_get"></a>  money_get:: do_get  
 虛擬函式，呼叫以從代表貨幣值的字元序列擷取數值。  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const virtual iter_type do_get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const
```  
  
### <a name="parameters"></a>參數  
 `first`  
 輸入迭代器定址序列，要轉換的開頭。  
  
 `last`  
 輸入迭代器定址轉換序列的結尾。  
  
 `_Intl`  
 布林值，指出應在序列中的貨幣符號的類型︰ **true** 如果國際 **false** 如果國內。  
  
 `_Iosbase`  
 格式旗標的時集指出的貨幣符號是選擇性的。否則，就是必要的。  
  
 `_State`  
 適當的位元遮罩設定的資料流狀態，根據作業是否成功。  
  
 `val`  
 字串，儲存已轉換的序列。  
  
### <a name="return-value"></a>傳回值  
 輸入迭代器定址貨幣輸入欄位之外的第一個項目。  
  
### <a name="remarks"></a>備註  
 第一個受保護的虛擬成員函式會嘗試比對循序開始第一個序列中的項目 [ `first`, ，`last`) 之前已辨識的完整，nonempty 貨幣輸入欄位。 如果成功，它會將此欄位一連串的一或多個十進位數字可以選擇性加上負號 ( `–`)，以代表數量，並將導致 [string_type](#money_get__string_type) 物件 `val`。 它會傳回迭代器指定貨幣輸入欄位之外的第一個項目。 否則，函式會儲存在空序列 `val` ，並設定 `ios_base::failbit` 中 `_State`。 它會傳回迭代器指定任何前置詞的有效貨幣輸入欄位之外的第一個項目。 在任一情況下，如果傳回的值等於 `last`, ，函式集合 `ios_base::eofbit` 中 `_State`。  
  
 第二個受保護的虛擬成員函式的行為與第一個相同之處在於如果成功轉換選擇性帶正負號的數字順序為型別的值 `long double` ，並將此值於 `val`。  
  
 貨幣輸入欄位的格式取決於 [地區設定 facet](../standard-library/locale-class.md#facet_class)**fac** 有效的呼叫所傳回的 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, ，**intl**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。  
  
 尤其是：  
  
- **fac**。 [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) 決定元件之欄位的出現的順序。  
  
- **fac**。 [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) 決定構成貨幣符號的項目序列。  
  
- **fac**。 [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) 決定項目的順序，顯示構成的正號。  
  
- **fac**。 [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) 決定項目的順序，顯示構成負號。  
  
- **fac**。 [群組](../standard-library/moneypunct-class.md#moneypunct__grouping) 決定小數點左邊數字的分組方式。  
  
- **fac**。 [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) 決定分隔小數點左邊數字群組的項目。  
  
- **fac**。 [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) 決定分隔整數位數與小數位數的項目。  
  
- **fac**。 [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) 決定要在小數點右邊的重要的小數位數數目。 當剖析具有多個小數位數不會針對呼叫的金額 `frac_digits`, ，`do_get` 就會停止剖析耗用最多之後 `frac_digits` 字元。  
  
 如果簽署字串 ( **fac**。 `negative_sign` 或 **fac**。 `positive_sign`) 有一個以上的項目，第一個項目符合其中的項目等於 **money_base::sign** 會出現在格式模式 ( **fac**。 `neg_format`). 任何其餘的項目會比對結尾的貨幣輸入欄位。 如果字串不符合貨幣輸入欄位中的下一個項目之第一個項目，簽署字串取得為空白，而正負號為正數。  
  
 如果 **iosbase**。 [旗標](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) 為非零值，此字串 **fac**。 `curr_symbol` 必須符合位置的項目等於 **money_base::symbol** 會出現在格式模式。 否則，如果 **money_base::symbol** 結尾的格式模式，就會發生，如果要比對不保留正負號的字串的任何項目，貨幣符號不相符。 否則，選擇性地比對的貨幣符號。  
  
 如果沒有執行個體的 **fac**。 `thousands_sep` 貨幣輸入欄位的值部分中發生 (其中的項目等於 **money_base::value** 會出現在格式模式)，加諸沒有群組的條件約束。 群組中的任何條件約束，否則所加諸 **fac**。 **群組** 會強制執行。 請注意，所產生的數字順序代表整數的低序位 **fac**。 `frac_digits` 十進位數字會被視為小數點右邊。  
  
 比對任何泛空白字元其中的項目等於 **money_base::space** 會出現在格式模式中，如果有出現以外的格式模式的結尾。 否則，會比不對任何內部空白字元。 項目 *ch* 會被視為泛空白字元，如果 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [ctype](../standard-library/ctype-class.md)\< **CharType**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 [是](../standard-library/ctype-class.md#ctype__is)( **ctype_base::space**, ，*ch*) 是 **true**。  
  
### <a name="example"></a>範例  
  請參閱範例 [取得](#money_get__get), ，而它會呼叫 `do_get`。  
  
##  <a name="a-namemoneygetgeta-moneygetget"></a><a name="money_get__get"></a>  money_get:: get  
 從代表貨幣值的字元序列擷取數值。  
  
```
iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(iter_type first,
    iter_type last,
    bool _Intl,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    string_type& val) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 輸入迭代器定址序列，要轉換的開頭。  
  
 `last`  
 輸入迭代器定址轉換序列的結尾。  
  
 `_Intl`  
 布林值，指出應在序列中的貨幣符號的類型︰ **true** 如果國際 **false** 如果國內。  
  
 `_Iosbase`  
 格式旗標的時集指出的貨幣符號是選擇性的。否則，便需要  
  
 `_State`  
 適當的位元遮罩設定的資料流狀態，根據作業是否成功。  
  
 `val`  
 字串，儲存已轉換的序列。  
  
### <a name="return-value"></a>傳回值  
 輸入迭代器定址貨幣輸入欄位之外的第一個項目。  
  
### <a name="remarks"></a>備註  
 這兩個成員函式會傳回 [do_get](#money_get__do_get)( `first``,` `last``,` `_Intl`, ，`_Iosbase`, ，`_State`, ，`val`)。  
  
### <a name="example"></a>範例  
  
```  
// money_get_get.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
  
int main( )  
{  
   locale loc( "german_germany" );  
  
   basic_stringstream< char > psz;  
   psz << use_facet<moneypunct<char, 1> >(loc).curr_symbol() << "-1.000,56";  
   basic_stringstream< char > psz2;  
   psz2 << "-100056" << use_facet<moneypunct<char, 1> >(loc).curr_symbol();  
  
   ios_base::iostate st = 0;  
   long double fVal;  
  
   psz.flags( psz.flags( )|ios_base::showbase );   
   // Which forced the READING the currency symbol  
   psz.imbue(loc);  
   use_facet < money_get < char > >( loc ).  
      get( basic_istream<char>::_Iter( psz.rdbuf( ) ),     
           basic_istream<char>::_Iter( 0 ), true, psz, st, fVal );  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz.str( ) << ", intl = 1) FAILED"  
           << endl;  
   else  
      cout << "money_get(" << psz.str( ) << ", intl = 1) = "   
           << fVal/100.0 << endl;  
  
   use_facet < money_get < char > >( loc ).  
      get(basic_istream<char>::_Iter(psz2.rdbuf( )),     
          basic_istream<char>::_Iter(0), false, psz2, st, fVal);  
  
   if ( st & ios_base::failbit )  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) FAILED"   
           << endl;  
   else  
      cout << "money_get(" << psz2.str( ) << ", intl = 0) = "   
           << fVal/100.0 << endl;  
};  
```  
  
##  <a name="a-namemoneygetitertypea-moneygetitertype"></a><a name="money_get__iter_type"></a>  money_get:: iter_type  
 描述輸入迭代器的類型。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **InputIterator**。  
  
##  <a name="a-namemoneygetmoneygeta-moneygetmoneyget"></a><a name="money_get__money_get"></a>  money_get:: money_get  
 `money_get` 類型物件的建構函式，用來從表示貨幣值的序列擷取數值。  
  
```
explicit money_get(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 用來指定物件的記憶體管理類型的整數值。  
  
### <a name="remarks"></a>備註  
 可能值 `_Refs` 參數和其重要性為︰  
  
-   0︰ 物件存留期由包含它的地區設定。  
  
-   1︰ 必須以手動方式管理物件存留期。  
  
-   \> 0︰ 未定義這些值。  
  
 因為解構函式會受到保護，是可行的沒有直接的範例。  
  
 建構函式初始化具有其基底物件 **地區設定::**[facet](../standard-library/locale-class.md#facet_class)( **_***Refs*)。  
  
##  <a name="a-namemoneygetstringtypea-moneygetstringtype"></a><a name="money_get__string_type"></a>  money_get:: string_type  
 類型，描述包含型別字元的字串 **CharType**。  
  
```
typedef basic_string<CharType, Traits, Allocator> string_type;
```  
  
### <a name="remarks"></a>備註  
 此類型描述範本類別的特製化 [basic_string](../standard-library/basic-string-class.md)。  
  
## <a name="see-also"></a>另請參閱  
 [\< 地區設定>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



