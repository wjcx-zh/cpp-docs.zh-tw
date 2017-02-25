---
title: "money_put 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std::money_put"
  - "xlocmon/std::money_put"
  - "money_put"
  - "std.money_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "money_put 類別"
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
caps.latest.revision: 19
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 19
---
# money_put 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以控制貨幣值轉換為類型 `CharType` 的序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class money_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
 `OutputIterator`  
 貨幣 put 函式將其輸出寫入其中的迭代器類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼。**  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[money_put](#money_put__money_put)|`money_put` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#money_put__char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#money_put__iter_type)|描述輸出迭代器的類型。|  
|[string_type](#money_put__string_type)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_put](#money_put__do_put)|虛擬函式，呼叫以將數字或字串轉換為代表貨幣值的字元序列。|  
|[放置](#money_put__put)|將數字或字串轉換為代表貨幣值的字元序列。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namemoneyputchartypea-moneyputchartype"></a><a name="money_put__char_type"></a>  money_put:: char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType**。  
  
##  <a name="a-namemoneyputdoputa-moneyputdoput"></a><a name="money_put__do_put"></a>  money_put:: do_put  
 虛擬函式，呼叫以將數字或字串轉換為代表貨幣值的字元序列。  
  
```  
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
virtual iter_type do_put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>參數  
 ` next`  
 迭代器定址插入字串的第一個元素中。  
  
 `_Intl`  
 布林值，指出應在序列中的貨幣符號的類型︰ **true** 如果國際 **false** 如果國內。  
  
 `_Iosbase`  
 格式旗標的時集指出的貨幣符號是選擇性的。否則，便需要  
  
 `_Fill`  
 用做為空格字元。  
  
 ` val`  
 要轉換的字串物件。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器所產生的位址超過最後一個項目的其中一個位置。  
  
### <a name="remarks"></a>備註  
 第一個受保護的虛擬成員函式會產生連續的項目開始 ` next` 產生貨幣輸出欄位從 [string_type](#money_put__string_type) 物件 ` val`。 所控制的序列 ` val` 必須以一個或多個十進位數字可以選擇性加上減號 （-），表示量。 函數會傳回迭代器，指定產生的貨幣輸出欄位之外的第一個項目。  
  
 第二個受保護的虛擬成員函式的行為與第一個相同除外，就第一個有效地將 ` val` 一連串的十進位數字，可以選擇性加上負號，然後將轉換為上述該序列。  
  
 貨幣輸出欄位的格式由 [地區設定 facet](../standard-library/locale-class.md#facet_class) （有效） 的呼叫所傳回的 fac [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, ，**intl**>> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。  
  
 尤其是：  
  
- **fac**。 [pos_format](../standard-library/moneypunct-class.md#moneypunct__pos_format) 決定產生的非負值的元件之欄位的順序。  
  
- **fac**。 [neg_format](../standard-library/moneypunct-class.md#moneypunct__neg_format) 決定欄位的元件產生負數值的順序。  
  
- **fac**。 [curr_symbol](../standard-library/moneypunct-class.md#moneypunct__curr_symbol) 決定產生的貨幣符號的項目序列。  
  
- **fac**。 [positive_sign](../standard-library/moneypunct-class.md#moneypunct__positive_sign) 決定要為正號產生的項目順序。  
  
- **fac**。 [negative_sign](../standard-library/moneypunct-class.md#moneypunct__negative_sign) 決定要為負號產生的項目順序。  
  
- **fac**。 [群組](../standard-library/moneypunct-class.md#moneypunct__grouping) 決定小數點左邊數字的分組方式。  
  
- **fac**。 [thousands_sep](../standard-library/moneypunct-class.md#moneypunct__thousands_sep) 決定分隔小數點左邊數字群組的項目。  
  
- **fac**。 [decimal_point](../standard-library/moneypunct-class.md#moneypunct__decimal_point) 決定分隔整數位數與任何小數位數的項目。  
  
- **fac**。 [frac_digits](../standard-library/moneypunct-class.md#moneypunct__frac_digits) 決定要在小數點右邊的重要的小數位數數目。  
  
 如果簽署字串 ( **fac**。 `negative_sign` 或 **fac**。 `positive_sign`) 有一個以上的項目，第一個項目，就會產生的項目等於 **money_base::sign** 會出現在格式模式 ( **fac**。 `neg_format` 或 **fac**。 `pos_format`). 貨幣輸出欄位的結尾，會產生任何其餘的項目。  
  
 如果 **iosbase**。 [旗標](../standard-library/ios-base-class.md#ios_base__flags) & [showbase](../Topic/%3Cios%3E%20functions.md#showbase) 為非零值，此字串 **fac**。 `curr_symbol` 會產生其中的項目等於 **money_base::symbol** 會出現在格式模式。 否則，會不產生任何貨幣符號。  
  
 如果沒有群組條件約束所加諸 **fac**。 **群組** （其第一個項目具有值 CHAR_MAX），然後的執行個體 **fac**。 `thousands_sep` 貨幣輸出欄位的值部分會產生 (其中的項目等於 **money_base::value** 會出現在格式模式)。 如果 **fac**。 `frac_digits` 是零，則不執行個體的 **fac**。 `decimal_point` 十進位數字之後所產生。 否則，產生的貨幣輸出欄位將低序位 **fac**。 `frac_digits` 要在小數點右邊的小數位數。  
  
 與邊框距離就會發生與任何數字的輸出欄位，除非該 **iosbase**。 **旗標** & **iosbase**。 [內部](../Topic/%3Cios%3E%20functions.md#internal) 為非零的所有內部填補，會產生相等的項目 **money_base::space** 會出現在格式模式中，如果出現。 否則，內部填補早產生的序列。 填補字元是 **填滿**。  
  
 函式呼叫 **iosbase**。 **寬度**重欄位寬度設為零 (0)。  
  
### <a name="example"></a>範例  
  請參閱範例 [放](#money_put__put), ，其中的虛擬成員函式會呼叫 **放**。  
  
##  <a name="a-namemoneyputitertypea-moneyputitertype"></a><a name="money_put__iter_type"></a>  money_put:: iter_type  
 描述輸出迭代器的類型。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **OutputIterator。**  
  
##  <a name="a-namemoneyputmoneyputa-moneyputmoneyput"></a><a name="money_put__money_put"></a>  money_put:: money_put  
 `money_put` 類型物件的建構函式。  
  
```  
explicit money_put(size_t _Refs = 0);
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
  
 建構函式初始化具有其基底物件 **地區設定::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`)。  
  
##  <a name="a-namemoneyputputa-moneyputput"></a><a name="money_put__put"></a>  money_put:: put  
 將數字或字串轉換為代表貨幣值的字元序列。  
  
```  
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,   
    const string_type& val) const;

 
iter_type put(
    iter_type next,   
    bool _Intl,   
    ios_base& _Iosbase,  
    CharType _Fill,  
    long double val) const;
```  
  
### <a name="parameters"></a>參數  
 ` next`  
 迭代器定址插入字串的第一個元素中。  
  
 `_Intl`  
 布林值，指出應在序列中的貨幣符號的類型︰ **true** 如果國際 **false** 如果國內。  
  
 `_Iosbase`  
 格式旗標的時集指出的貨幣符號是選擇性的。否則，便需要  
  
 `_Fill`  
 用做為空格字元。  
  
 ` val`  
 要轉換的字串物件。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器所產生的位址超過最後一個項目的其中一個位置。  
  
### <a name="remarks"></a>備註  
 這兩個成員函式會傳回 [do_put](#money_put__do_put)( ` next`, ，`_Intl`, ，`_Iosbase`, ，`_Fill`, ，` val`)。  
  
### <a name="example"></a>範例  
  
```  
// money_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
//   locale loc( "german_germany" );  
   locale loc( "english_canada" );  
   basic_stringstream<char> psz, psz2;  
   ios_base::iostate st = 0;  
  
   psz2.imbue( loc );  
   psz2.flags( psz2.flags( )|ios_base::showbase ); // force the printing of the currency symbol  
   use_facet < money_put < char > >(loc).put(basic_ostream<char>::_Iter( psz2.rdbuf( ) ), true, psz2, st, 100012);  
   if (st & ios_base::failbit)  
      cout << "money_put( ) FAILED" << endl;  
   else  
      cout << "money_put( ) = \"" << psz2.rdbuf( )->str( ) <<"\""<< endl;     
  
   st = 0;  
};  
```  
  
```Output  
money_put( ) = "CAD1,000.12"  
```  
  
##  <a name="a-namemoneyputstringtypea-moneyputstringtype"></a><a name="money_put__string_type"></a>  money_put:: string_type  
 類型，描述包含型別字元的字串 **CharType**。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述範本類別的特製化 [basic_string](../standard-library/basic-string-class.md) 其物件可以儲存在來源序列中項目的序列。  
  
## <a name="see-also"></a>另請參閱  
 [\< 地區設定>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

