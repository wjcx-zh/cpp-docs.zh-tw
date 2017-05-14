---
title: "money_put 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xlocmon/std::money_put
- money_put
- locale/std::money_put::char_type
- locale/std::money_put::iter_type
- locale/std::money_put::string_type
- locale/std::money_put::do_put
- locale/std::money_put::put
dev_langs:
- C++
helpviewer_keywords:
- money_put class
ms.assetid: f439fd56-c9b1-414c-95e1-66c918c6eee6
caps.latest.revision: 19
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
ms.openlocfilehash: 825edc66a7b4b565222133ebb47a789efbdba52b
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="moneyput-class"></a>money_put 類別
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
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[money_put](#money_put)|`money_put` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#iter_type)|描述輸出迭代器的類型。|  
|[string_type](#string_type)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_put](#do_put)|虛擬函式，呼叫以將數字或字串轉換為代表貨幣值的字元序列。|  
|[put](#put)|將數字或字串轉換為代表貨幣值的字元序列。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="char_type"></a>  money_put::char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **CharType** 同義。  
  
##  <a name="do_put"></a>  money_put::do_put  
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
 `next`  
 迭代器，定址對象是所插入字串的第一個元素。  
  
 `_Intl`  
 布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。  
  
 `_Iosbase`  
 格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。  
  
 `_Fill`  
 間距所使用的字元。  
  
 `val`  
 要轉換的字串物件。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。  
  
### <a name="remarks"></a>備註  
 第一個虛擬的受保護成員函式會從 `next` 開始產生一系列元素，以從 [string_type](#string_type) 物件 `val` 產生貨幣輸出欄位。 所控制的序列`val`必須以一個或多個十進位的數字，選擇性地加上減號 （-），表示量開頭。 此函式會傳回迭代器，此迭代器指定所產生之貨幣輸出欄位後的第一個元素。  
  
 第二個虛擬受保護成員函式的行為與第一個相同，不同的是，它會先將 `val` 實際轉換成十進位數字的序列，視需要在前面加上減號，然後依上述方式轉換該序列。  
  
 貨幣輸出欄位的格式會由 [locale facet](../standard-library/locale-class.md#facet_class) fac (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [moneypunct](../standard-library/moneypunct-class.md)\< **CharType**, **intl**> >( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 有效呼叫所傳回) 決定。  
  
 尤其是：  
  
- **fac**. [pos_format](../standard-library/moneypunct-class.md#pos_format) 會決定為非負數值產生欄位元件時的順序。  
  
- **fac**. [neg_format](../standard-library/moneypunct-class.md#neg_format) 會決定為負數值產生欄位元件時的順序。  
  
- **fac**. [curr_symbol](../standard-library/moneypunct-class.md#curr_symbol) 會決定要為貨幣符號產生的元素序列。  
  
- **fac**. [positive_sign](../standard-library/moneypunct-class.md#positive_sign) 會決定要為正號產生的元素序列。  
  
- **fac**. [negative_sign](../standard-library/moneypunct-class.md#negative_sign) 會決定要為負號產生的元素序列。  
  
- **fac**. [grouping](../standard-library/moneypunct-class.md#grouping) 會決定任何小數點左邊數字分組的方式。  
  
- **fac**. [thousands_sep](../standard-library/moneypunct-class.md#thousands_sep) 會決定任何小數點左邊分隔數字群組的元素。  
  
- **fac**. [decimal_point](../standard-library/moneypunct-class.md#decimal_point) 會決定將整數與任何小數分隔的元素。  
  
- **fac**. [frac_digits](../standard-library/moneypunct-class.md#frac_digits) 會決定任何小數點右邊的有效小數數目。  
  
 如果正負號字串 ( **fac**. `negative_sign` 或 **fac**. `positive_sign`) 有多個元素，將只會在格式模式中與 **money_base::sign** 相等之元素出現的位置，產生第一個元素，其中該格式模式為 ( **fac**. `neg_format` 或 **fac**. `pos_format`)。 所有其餘元素則是在貨幣輸入欄位的結尾產生。  
  
 如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & [showbase](../standard-library/ios-functions.md#showbase) 不為零，字串 **fac**. `curr_symbol` 就會在格式模式中與 **money_base::symbol** 相等之元素出現的位置產生。 否則，不會產生任何貨幣符號。  
  
 如果 **fac**. **grouping** (其第一個元素的值為 CHAR_MAX) 未施加任何千分號條件約束，就不會有任何 **fac**. `thousands_sep` 執行個體在貨幣輸出欄位的值部分 (格式模式中與 **money_base::value** 相等之元素出現的位置) 產生。 如果 **fac**. `frac_digits` 為零，則在十進位數字之後不會產生任何 **fac**. `decimal_point` 執行個體。 否則，產生的貨幣輸出欄位會將低序位 **fac**. `frac_digits` 十進位數字放在小數點右邊。  
  
 系統會針對所有數字輸出欄位進行填補，但有例外，就是如果 **iosbase**. **flags** & **iosbase**. [internal](../standard-library/ios-functions.md#internal) 不為零，便會在格式模式中與 **money_base::space** 相等之元素出現的位置，於該元素未出現的情況下，產生任何內部填補字元。 否則，內部填補字元會出現在已產生的序列之前。 填補字元為 **fill**。  
  
 函式會呼叫 **iosbase**. **width**(0) 將欄位寬度重設為零。  
  
### <a name="example"></a>範例  
  請參閱 [put](#put) 的範例，其中會由 **put** 呼叫此虛擬成員函式。  
  
##  <a name="iter_type"></a>  money_put::iter_type  
 描述輸出迭代器的類型。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **OutputIterator** 同義。  
  
##  <a name="money_put"></a>  money_put::money_put  
 `money_put` 類型物件的建構函式。  
  
```  
explicit money_put(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 整數值，用來指定物件的記憶體管理類型。  
  
### <a name="remarks"></a>備註  
 `_Refs` 參數的可能值和其意義如下：  
  
-   0：物件的存留期由包含該物件的地區設定來管理。  
  
-   1：物件的存留期必須以手動方式管理。  
  
-   \>1︰ 未定義這些值。  
  
 無法提供任何直接範例，因為解構函式受到保護。  
  
 建構函式會以 **locale::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) 將其基底物件初始化。  
  
##  <a name="put"></a>  money_put::put  
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
 `next`  
 迭代器，定址對象是所插入字串的第一個元素。  
  
 `_Intl`  
 布林值，指出序列中預期的貨幣符號類型：如果是國際，即為 **true**，如果是國內，則為 **false**。  
  
 `_Iosbase`  
 格式旗標，已設定時，表示貨幣符號為選用；否則，必須指定貨幣符號。  
  
 `_Fill`  
 間距所使用的字元。  
  
 `val`  
 要轉換的字串物件。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器，定址對象是所產生之最後一個元素的後面一個位置。  
  
### <a name="remarks"></a>備註  
 兩個成員函式都會傳回 [do_put](#do_put)( `next`, `_Intl`, `_Iosbase`, `_Fill`, `val`)。  
  
### <a name="example"></a>範例  
  
```cpp  
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
  
##  <a name="string_type"></a>  money_put::string_type  
 一種類型，描述包含 **CharType** 類型字元的字串。  
  
```  
typedef basic_string<CharType, Traits, Allocator> string_type;  
```  
  
### <a name="remarks"></a>備註  
 此類型描述 [basic_string](../standard-library/basic-string-class.md) 範本類別的特製化，其中此類別的物件可儲存來自來源序列的元素序列。  
  
## <a name="see-also"></a>另請參閱  
 [\<locale>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)


