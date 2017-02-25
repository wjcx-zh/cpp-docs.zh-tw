---
title: "num_get 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "num_get"
  - "std::num_get"
  - "std.num_get"
  - "xlocnum/std::num_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_get 類別"
ms.assetid: 9933735d-3918-4b17-abad-5fca2adc62d7
caps.latest.revision: 18
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 18
---
# num_get 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

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
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼。**  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[num_get](#num_get__num_get)|用來從序列擷取數值之 `num_get` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#num_get__char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#num_get__iter_type)|描述輸入迭代器的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_get](#num_get__do_get)|虛擬函式，呼叫以從字元序列擷取數值或布林值。|  
|[取得](#num_get__get)|從字元序列擷取數值或布林值。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namenumgetchartypea-numgetchartype"></a><a name="num_get__char_type"></a>  num_get:: char_type  
 類型，用來描述由地區設定使用的字元。  
  
```
typedef CharType char_type;
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType**。  
  
##  <a name="a-namenumgetdogeta-numgetdoget"></a><a name="num_get__do_get"></a>  num_get:: do_get  
 虛擬函式，呼叫以從字元序列擷取數值或布林值。  
  
```
virtual iter_type do_get(
    iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long& val) const;virtual iter_type do_get(
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
 要從中讀取數目的字元範圍的開頭。  
  
 `last`  
 要從中讀取數目的字元範圍的結尾。  
  
 `_Iosbase`  
  [Ios_base](../standard-library/ios-base-class.md) 轉換所使用的旗標。  
  
 `_State`  
 哪些 failbit 後的狀態 (請參閱 [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) 會在失敗時加入。  
  
 `val`  
 已讀取的值。  
  
### <a name="return-value"></a>傳回值  
 迭代器在讀取值之後。  
  
### <a name="remarks"></a>備註  
 第一個受保護的虛擬成員函式  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long& val`  
  
 `) const;`  
  
 比對開頭的項目循序 `first` 序列中 `[``first``,` `last``)` 之前已辨識的完整，非空白的整數輸入欄位。 如果成功，它會將此欄位類型為其相等的值 `long``,` ，並將結果 `val`。 它會傳回迭代器指定數字輸入欄位之外的第一個項目。 否則，函數會儲存在中為 nothing `val` ，並設定 `ios_base::failbit` 中 `state`。 它會傳回迭代器指定有效的整數的輸入任何的欄位前置詞之外的第一個項目。 在任一情況下，如果傳回的值等於 `last`, ，函式集合 `ios_base::eofbit` 中 `state`。  
  
 比對和轉換的一系列的掃描函式使用相同的規則轉換成整數的輸入的欄位 `char` 檔案中的項目。 (每個這類 `char` 項目會對應至對等項目類型的假設 `Elem` 的簡單一對一時，由對應。)對等的掃描轉換規格的決定方式如下︰  
  
 如果 `iosbase.`[ios_base:: flags](../standard-library/ios-base-class.md#ios_base__flags)`() & ios_base::basefield == ios_base::`[年 10 月](../Topic/%3Cios%3E%20functions.md#oct), ，轉換規格的 `lo`。  
  
 如果 `iosbase.flags() & ios_base::basefield == ios_base::`[十六進位](../Topic/%3Cios%3E%20functions.md#hex), ，轉換規格的 `lx`。  
  
 如果 `iosbase.flags() & ios_base::basefield == 0`, ，轉換規格的 `li`。  
  
 否則，轉換規格是 `ld`。  
  
 整數輸入欄位的格式進一步由 [地區設定 facet](../standard-library/locale-class.md#facet_class)`fac` 呼叫所傳回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) `<`[numpunct](../standard-library/numpunct-class.md)`<Elem>(iosbase.` [ios_base:: getloc](../standard-library/ios-base-class.md#ios_base__getloc)`())`。 尤其是：  
  
 `fac.` [numpunct:: grouping](../standard-library/numpunct-class.md#numpunct__grouping) `()` 決定小數點左邊數字的分組方式  
  
 `fac.` [numpunct:: thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) `()` 分隔小數點左邊數字群組的順序決定。  
  
 如果沒有執行個體的 `fac.thousands_sep()` 沒有群組的條件約束不會加上在數字輸入欄位中，會發生。 群組中的任何條件約束，否則所加諸 `fac.grouping()` 會強制執行並掃描轉換發生之前移除分隔符號。  
  
 第四個的受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long& val`  
  
 `) const;`  
  
 行為與第一個相同，不同之處在於它會取代轉換規格的 `ld` 與 `lu`。 如果成功會將轉換的數字輸入的欄位值的型別 `unsigned long` ，並將此值於 `val`。  
  
 第五個的受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long long& val`  
  
 `) const;`  
  
 行為與第一個相同，不同之處在於它會取代轉換規格的 `ld` 與 `lld`。 如果成功會將轉換的數字輸入的欄位值的型別 `long long` ，並將此值於 `val`。  
  
 第六個的受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `unsigned long long& val`  
  
 `) const;`  
  
 行為與第一個相同，不同之處在於它會取代轉換規格的 `ld` 與 `llu`。 如果成功會將轉換的數字輸入的欄位值的型別 `unsigned long long` ，並將此值於 `val`。  
  
 第七個的受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `float& val`  
  
 `) const;`  
  
 不同之處在於它儘量符合完整的非空白浮點輸入的欄位的行為與第一個相同。 `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` 分隔整數位數與小數位數的順序決定。 對等的掃描轉換規範， `lf`。  
  
 第八個受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `double& val`  
  
 `) const;`  
  
 不同之處在於它儘量符合完整的非空白浮點輸入的欄位的行為與第一個相同。 `fac.`[numpunct:: decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point)`()` 分隔整數位數與小數位數的順序決定。 對等的掃描轉換規範， `lf`。  
  
 第九個受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `long double& val`  
  
 `) const;`  
  
 行為和第八、 一樣，只不過是對等的掃描轉換規範 `Lf`。  
  
 第九個受保護的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `void *& val`  
  
 `) const;`  
  
 行為相同第一，但對等的掃描轉換規範 `p`。  
  
 最後一個的受保護的 （第十一個） 的虛擬成員函式︰  
  
 `virtual iter_type do_get(`  
  
 `iter_type first,`  
  
 `iter_type last,`  
  
 `ios_base& _Iosbase,`  
  
 `ios_base::iostate& _State,`  
  
 `bool& val`  
  
 `) const;`  
  
 不同之處在於它儘量符合完整的非空白布林輸入的欄位的行為與第一個相同。 如果成功會將轉換的布林值的輸入的欄位值的型別 `bool` ，並將此值於 `val`。  
  
 布林值的輸入的欄位會有兩種形式。 如果 `iosbase.flags() & ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 為 false，它會是做為整數的輸入欄位，相同轉換的值必須是 0 (false) 或 1 (true)。 否則，順序必須符合 `fac.`[numpunct:: falsename](../standard-library/numpunct-class.md#numpunct__falsename)`()` （適用於 false)，或 `fac.`[numpunct:: truename](../standard-library/numpunct-class.md#numpunct__truename)`()` （如 true)。  
  
### <a name="example"></a>範例  
  請參閱範例 [取得](#num_get__get), ，其中的虛擬成員函式會呼叫 `do_get`。  
  
##  <a name="a-namenumgetgeta-numgetget"></a><a name="num_get__get"></a>  num_get:: get  
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
 要從中讀取數目的字元範圍的開頭。  
  
 `last`  
 要從中讀取數目的字元範圍的結尾。  
  
 `_Iosbase`  
  [Ios_base](../standard-library/ios-base-class.md) 轉換所使用的旗標。  
  
 `_State`  
 哪些 failbit 後的狀態 (請參閱 [ios_base:: iostate](../standard-library/ios-base-class.md#ios_base__iostate)) 會在失敗時加入。  
  
 `val`  
 已讀取的值。  
  
### <a name="return-value"></a>傳回值  
 迭代器在讀取值之後。  
  
### <a name="remarks"></a>備註  
 所有成員函式會都傳回 [do_get](#num_get__do_get)( `first`, ，`last`, ，`_Iosbase`, ，`_State`, ，`val`)。  
  
 第一個受保護的虛擬成員函式會嘗試比對循序開始第一個序列中的項目 [ `first`, ，`last`) 之前已辨識的完整，非空白的整數輸入欄位。 如果成功，它會將此欄位類型為其相等的值 **長** ，並將結果 `val`。 它會傳回迭代器指定數字輸入欄位之外的第一個項目。 否則，函數會儲存在中為 nothing `val` ，並設定 `ios_base::failbit` 中 _ *狀態*。 它會傳回迭代器指定有效的整數的輸入任何的欄位前置詞之外的第一個項目。 在任一情況下，如果傳回的值等於 **上次**, ，函式集合 `ios_base::eofbit` 中 `_State`。  
  
 比對和轉換的一系列的掃描函式使用相同的規則轉換成整數的輸入的欄位 `char` 檔案中的項目。 每個這類 `char` 項目會對應至對等項目類型的假設 **CharType** 簡單的一對一對應。 對等的掃描轉換規格的決定方式如下︰  
  
-   如果 **iosbase**。 [旗標](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[年 10 月](../Topic/%3Cios%3E%20functions.md#oct), ，轉換規格的 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[十六進位](../Topic/%3Cios%3E%20functions.md#hex), ，轉換規格的 **lx**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** = = 0，轉換規格的 `li`。  
  
-   否則，就是轉換規格 **ld**。  
  
 整數輸入欄位的格式進一步由 [地區設定 facet](../standard-library/locale-class.md#facet_class)**fac** 呼叫所傳回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 尤其是：  
  
- **fac**。 [群組](../standard-library/numpunct-class.md#numpunct__grouping) 決定小數點左邊數字的分組方式。  
  
- **fac**。 [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) 分隔小數點左邊數字群組的順序決定。  
  
 如果沒有執行個體的 **fac**。 `thousands_sep` 數字輸入欄位中，沒有群組的條件約束不會加上。 群組中的任何條件約束，否則所加諸 **fac**。 **群組** 會強制執行並掃描轉換發生之前移除分隔符號。  
  
 第二個的受保護的虛擬成員函式︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    unsigned long& val) const;
```  
  
 不同之處在於它會取代轉換規格的行為與第一個相同 **ld** 與 **lu**。 如果成功，它會將數字輸入的欄位型別的值 `unsigned long` ，並將此值於 `val`。  
  
 第三個受保護的虛擬成員函式︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    double& val) const;
```  
  
 不同之處在於它會嘗試比對的完整的非空白浮點輸入的欄位的行為與第一個相同。 **fac**。 [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) 分隔整數位數與小數位數的順序決定。 對等的掃描轉換規範， **lf**。  
  
 第四個的受保護的虛擬成員函式︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    long double& val) const;
```  
  
 行為相同第三個，但對等的掃描轉換規範， **Lf**。  
  
 第五個的受保護的虛擬成員函式︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    void *& val) const;
```  
  
 行為相同第一，但對等的掃描轉換規範 **p**。  
  
 第六個的受保護的虛擬成員函式︰  
  
```
virtual iter_type do_get(iter_type first,
    iter_type last,
    ios_base& _Iosbase,
    ios_base::iostate& _State,
    bool& val) const;
```  
  
 不同之處在於它會嘗試比對的完整的非空白布林輸入的欄位的行為與第一個相同。 如果成功會將轉換的布林值的輸入的欄位值的型別 `bool` ，並將此值於 `val`。  
  
 布林值的輸入的欄位會有兩種形式。 如果 **iosbase**。 **旗標** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 是 **false**, ，它做為整數的輸入欄位，相同之處在於轉換的值必須是 0 (如 **false**) 或 1 (如 **true**)。 否則，順序必須符合 **fac**。 [falsename](../standard-library/numpunct-class.md#numpunct__falsename) (如 **false**)，或 **fac**。 [truename](../standard-library/numpunct-class.md#numpunct__truename) (如 **true**)。  
  
### <a name="example"></a>範例  
  
```  
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
  
##  <a name="a-namenumgetitertypea-numgetitertype"></a><a name="num_get__iter_type"></a>  num_get:: iter_type  
 描述輸入迭代器的類型。  
  
```
typedef InputIterator iter_type;
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **InputIterator**。  
  
##  <a name="a-namenumgetnumgeta-numgetnumget"></a><a name="num_get__num_get"></a>  num_get:: num_get  
 用來從序列擷取數值之 `num_get` 類型物件的建構函式。  
  
```
explicit num_get(size_t _Refs = 0);
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
  
## <a name="see-also"></a>另請參閱  
 [\< 地區設定>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)



