---
title: "num_get 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- num_get
- xlocnum/std::num_get
- locale/std::num_get::char_type
- locale/std::num_get::iter_type
- locale/std::num_get::do_get
- locale/std::num_get::get
dev_langs:
- C++
helpviewer_keywords:
- num_get class
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
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
ms.openlocfilehash: f8595909a294775034c3e1b725d37bfe0f846a93
ms.contentlocale: zh-tw
ms.lasthandoff: 04/29/2017

---
# <a name="numget-class"></a>num_get 類別
樣板類別，描述可以做為地區設定 facet 的物件，以控制類型 `CharType` 的序列轉換為數值。  
  
## <a name="syntax"></a>語法  
  
```
template <class CharType, class InputIterator = istreambuf_iterator<CharType>>  
class num_get : public locale::facet;
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
 `InputIterator`  
 數值 get 函式從中讀取其輸入的迭代器類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存值時，會在 **id** 中儲存一個唯一的正值。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[num_get](#num_get)|用來從序列擷取數值之 `num_get` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#iter_type)|描述輸入迭代器的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_get](#do_get)|虛擬函式，呼叫以從字元序列擷取數值或布林值。|  
|[get](#get)|從字元序列擷取數值或布林值。|  
  
## <a name="requirements"></a>需求  
 **標頭︰**\<locale>  
  
 **命名空間：** std  
  
##  <a name="char_type"></a>  num_get::char_type  
 類型，用來描述由地區設定使用的字元。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **CharType** 同義。  
  
##  <a name="do_get"></a>  num_get::do_get  
 虛擬函式，呼叫以從字元序列擷取數值或布林值。  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
    
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;

virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要從中讀取數字的字元範圍開頭。  
  
 `last`  
 要從中讀取數字的字元範圍結尾。  
  
 `_Iosbase`  
 旗標供轉換使用的 [ios_base](../standard-library/ios-base-class.md)。  
  
 `_State`  
 失敗時會新增 failbit (請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) 的狀態。  
  
 `val`  
 已讀取的值。  
  
### <a name="return-value"></a>傳回值  
 已讀取值之後的迭代器。  
  
### <a name="remarks"></a>備註  
 第一個虛擬的受保護成員函式  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;
```  
  
 比對開始的循序項目`first`序列中`[first, last)`直到它卻被完整，非空白的整數輸入欄位。 如果成功，它會將轉換此欄位類型為其相等的值`long`，並將導致`val`。 它會傳回迭代器，此迭代器指定數字輸入欄位後的第一個元素。 否則，函式不會在 `val` 中儲存任何內容，並會在 `state` 中設定 `ios_base::failbit`。 它會傳回迭代器，此迭代器指定有效整數輸入欄位之任何前置詞後的第一個元素。 不論是上述哪一種情況，如果傳回值等於 `last`，函式就會在 `state` 中設定 `ios_base::eofbit`。  
  
 轉換整數輸入欄位的規則，與掃描函式在比對及轉換來自某個檔案的一系列 `char` 元素時所使用的規則相同。 (每個這類 `char` 元素都會被假設為與 `Elem` 類型的對等元素以簡單、一對一的對應方式對應)。對等的掃描轉換規格是以下列方式決定：  
  
 如果 `iosbase.`[ios_base::flags](../standard-library/ios-base-class.md#flags)`() & ios_base::basefield == ios_base::`[oct](../standard-library/ios-functions.md#oct)，則轉換規格為 `lo`。  
  
 如果 `iosbase.flags() & ios_base::basefield == ios_base::`[hex](../standard-library/ios-functions.md#hex)，則轉換規格為 `lx`。  
  
 如果 `iosbase.flags() & ios_base::basefield == 0`，則轉換規格為 `li`。  
  
 否則，轉換規格會是 `ld`。  
  
 整數輸入欄位的格式會進一步由 [use_facet](../standard-library/locale-functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base::getloc](../standard-library/ios-base-class.md#getloc)`())` 呼叫所傳回的 [locale facet](../standard-library/locale-class.md#facet_class)`fac` 決定。 尤其是：  
  
 `fac.` [numpunct::grouping](../standard-library/numpunct-class.md#grouping) `()` 會決定任何小數點左邊數字分組的方式  
  
 `fac.` [numpunct::thousands_sep](../standard-library/numpunct-class.md#thousands_sep) `()` 會決定任何小數點左邊分隔數字群組的序列。  
  
 如果沒有任何 `fac.thousands_sep()` 執行個體出現在數字輸入欄位中，就不會施加任何千分號條件約束。 否則，將會強制執行 `fac.grouping()` 所施加的任何千分號條件約束，並在進行掃描轉換之前將分隔符號移除。  
  
 第四個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 行為與第一個相同，不同的是，它會以 `lu` 取代 `ld` 轉換規格。 如果成功，它就會將數字輸入欄位轉換成 `unsigned long` 類型的值，並將該值儲存在 `val` 中。  
  
 第五個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;
```  
  
 行為與第一個相同，不同的是，它會以 `lld` 取代 `ld` 轉換規格。 如果成功，它就會將數字輸入欄位轉換成 `long long` 類型的值，並將該值儲存在 `val` 中。  
  
 第六個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;
```  

 行為與第一個相同，不同的是，它會以 `llu` 取代 `ld` 轉換規格。 如果成功，它就會將數字輸入欄位轉換成 `unsigned long long` 類型的值，並將該值儲存在 `val` 中。  
  
 第七個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;
```  
  
 行為與第一個相同，不同的是，它會盡力比對出完整、非空白的浮點數輸入欄位。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 會決定將整數與小數分隔的序列。 對等掃描轉換指定名稱是 `lf`。  
  
 第八個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 行為與第一個相同，不同的是，它會盡力比對出完整、非空白的浮點數輸入欄位。 `fac.`[numpunct::decimal_point](../standard-library/numpunct-class.md#decimal_point)`()` 會決定將整數與小數分隔的序列。 對等掃描轉換指定名稱是 `lf`。  
  
 第九個虛擬的受保護成員函式：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行為與第八個相同，不同的是，對等掃描轉換指定名稱是 `Lf`。  
  
 第十個受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 行為與第一個相同，不同的是，對等掃描轉換指定名稱是 `p`。  
  
 最後一個 (第十一個) 虛擬的受保護成員函式：  
  
```  
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 行為與第一個相同，不同的是，它會盡力比對出完整、非空白的布林值輸入欄位。 如果成功，它就會將布林值輸入欄位轉換成 `bool` 類型的值，並將該值儲存在 `val` 中。  
  
 布林值輸入欄位採用下列兩種形式其中之一。 如果 `iosbase.flags() & ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 為 false，它就與整數輸入欄位相同，不同的是，轉換的值必須是 0 (代表 false) 或 1 (代表 true)。 否則，序列必須與 `fac.`[numpunct::falsename](../standard-library/numpunct-class.md#falsename)`()` (代表 false) 或 `fac.`[numpunct::truename](../standard-library/numpunct-class.md#truename)`()` (代表 true) 相符。  
  
### <a name="example"></a>範例  
  請參閱 [get](#get) 的範例，其中會由 `do_get` 呼叫此虛擬成員函式。  
  
##  <a name="get"></a>  num_get::get  
 從字元序列擷取數值或布林值。  
  
```
iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned short& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned int& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long long& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    float& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;

iter_type get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
### <a name="parameters"></a>參數  
 `first`  
 要從中讀取數字的字元範圍開頭。  
  
 `last`  
 要從中讀取數字的字元範圍結尾。  
  
 `_Iosbase`  
 旗標供轉換使用的 [ios_base](../standard-library/ios-base-class.md)。  
  
 `_State`  
 失敗時會新增 failbit (請參閱 [ios_base::iostate](../standard-library/ios-base-class.md#iostate)) 的狀態。  
  
 `val`  
 已讀取的值。  
  
### <a name="return-value"></a>傳回值  
 已讀取值之後的迭代器。  
  
### <a name="remarks"></a>備註  
 所有成員函式都會傳回 [do_get](#do_get)( `first`, `last`, `_Iosbase`, `_State`, `val`)。  
  
 第一個虛擬的受保護成員函式會嘗試比對序列 [ `first`, `last`) 中從 first 開始的一系列元素，直到它辨識出完整、非空白的整數輸入欄位為止。 如果成功，它就會將此欄位轉換成其 **long** 類型的對等值，並將結果儲存在 `val` 中。 它會傳回迭代器，此迭代器指定數字輸入欄位後的第一個元素。 否則，函式不會在 `val` 中儲存任何內容，並會在 _ *State* 中設定 `ios_base::failbit`。 它會傳回迭代器，此迭代器指定有效整數輸入欄位之任何前置詞後的第一個元素。 不論是上述哪一種情況，如果傳回值等於 **last**，函式就會在 `_State` 中設定 `ios_base::eofbit`。  
  
 轉換整數輸入欄位的規則，與掃描函式在比對及轉換來自某個檔案的一系列 `char` 元素時所使用的規則相同。 每個這類 `char` 元素都會被假設為與 **CharType** 類型的對等元素以簡單、一對一的對應方式對應。 對等的掃描轉換規格是以下列方式決定：  
  
-   如果 **iosbase**. [flags](../standard-library/ios-base-class.md#flags) & `ios_base::basefield` == `ios_base::`[oct](../standard-library/ios-functions.md#oct)，則轉換規格為 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[hex](../standard-library/ios-functions.md#hex)，則轉換規格為 **lx**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == 0，則轉換規格為 `li`。  
  
-   否則，轉換規格會是 **ld**。  
  
 整數輸入欄位的格式會進一步由 [locale facet](../standard-library/locale-class.md#facet_class)**fac** (由 [use_facet](../standard-library/locale-functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**>( **iosbase**. [getloc](../standard-library/ios-base-class.md#getloc)) 呼叫所傳回) 決定。 尤其是：  
  
- **fac**. [grouping](../standard-library/numpunct-class.md#grouping) 會決定任何小數點左邊數字分組的方式。  
  
- **fac**. [thousands_sep](../standard-library/numpunct-class.md#thousands_sep) 會決定任何小數點左邊分隔數字群組的序列。  
  
 如果沒有任何 **fac**. `thousands_sep` 執行個體出現在數字輸入欄位中，就不會施加任何千分號條件約束。 否則，將會強制執行 **fac**. **grouping** 所施加的任何千分號條件約束，並在進行掃描轉換之前將分隔符號移除。  
  
 第二個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 行為與第一個相同，不同的是，它會以 **lu** 取代 **ld** 轉換規格。 如果成功，它就會將數字輸入欄位轉換成 `unsigned long` 類型的值，並將該值儲存在 `val` 中。  
  
 第三個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 行為與第一個相同，不同的是，它會嘗試比對出完整、非空白的浮點數輸入欄位。 **fac**. [decimal_point](../standard-library/numpunct-class.md#decimal_point) 會決定將整數與小數分隔的序列。 對等掃描轉換指定名稱是 **lf**。  
  
 第四個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行為與第一個相同，不同的是，對等掃描轉換指定名稱是 **Lf**。  
  
 第五個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 行為與第一個相同，不同的是，對等掃描轉換指定名稱是 **p**。  
  
 第六個虛擬的受保護成員函式：  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 行為與第一個相同，不同的是，它會嘗試比對出完整、非空白的布林值輸入欄位。 如果成功，它就會將布林值輸入欄位轉換成 `bool` 類型的值，並將該值儲存在 `val` 中。  
  
 布林值輸入欄位採用下列兩種形式其中之一。 如果 **iosbase**. **flags** & `ios_base::`[boolalpha](../standard-library/ios-functions.md#boolalpha) 為 **false**，它就與整數輸入欄位相同，不同的是，轉換的值必須是 0 (代表 **false**) 或 1 (代表 **true**)。 否則，序列必須符合 **fac**. [falsename](../standard-library/numpunct-class.md#falsename) (代表 **false**) 或 **fac**. [truename](../standard-library/numpunct-class.md#truename) (代表 **true**)。  
  
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
  
##  <a name="iter_type"></a>  num_get::iter_type  
 描述輸入迭代器的類型。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>備註  
 此類型與範本參數 **InputIterator** 同義。  
  
##  <a name="num_get"></a>  num_get::num_get  
 用來從序列擷取數值之 `num_get` 類型物件的建構函式。  
  
```
explicit num_get(size_t _Refs = 0);
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
  
## <a name="see-also"></a>另請參閱  
 [\<locale>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)




