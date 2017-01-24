---
title: "num_put 類別 | Microsoft Docs"
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
  - "std::num_put"
  - "xlocnum/std::num_put"
  - "num_put"
  - "std.num_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "num_put 類別"
ms.assetid: 36c5bffc-8283-4201-8ed4-78c4d81f8a17
caps.latest.revision: 21
caps.handback.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# num_put 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別，描述可以做為地區設定 facet 的物件，以控制數值轉換為類型 `CharType` 的序列。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType,  
    class OutputIterator = ostreambuf_iterator<CharType>>  
class num_put : public locale::facet;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 程式內用於編碼地區設定字元的類型。  
  
 `OutputIterator`  
 數值 put 函式將其輸出寫入其中的迭代器類型。  
  
## <a name="remarks"></a>備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 **識別碼。**  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[num_put](#num_put__num_put)|`num_put` 類型物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[char_type](#num_put__char_type)|類型，用來描述由地區設定使用的字元。|  
|[iter_type](#num_put__iter_type)|描述輸出迭代器的類型。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[do_put](#num_put__do_put)|虛擬函式，呼叫以將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|  
|[放置](#num_put__put)|將數字轉換成 `CharType` 序列，表示為特定地區設定格式化的數字。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namenumputchartypea-numputchartype"></a><a name="num_put__char_type"></a>  num_put:: char_type  
 類型，用來描述由地區設定使用的字元。  
  
```  
typedef CharType char_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType**。  
  
##  <a name="a-namenumputdoputa-numputdoput"></a><a name="num_put__do_put"></a>  num_put:: do_put  
 虛擬函式，呼叫以將數字轉換成一連串的 **CharType**表示數字格式化為特定地區設定。  
  
```  
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;

 
virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const long long val) const;

virtual iter_type do_put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const unsigned long long val) const;
```  
  
### <a name="parameters"></a>參數  
 ` next`  
 迭代器定址插入字串的第一個元素中。  
  
 `_Iosbase`  
 指定資料流，其中包含與用來插入的輸出和格式化輸出的旗標 numpunct facet 的地區設定。  
  
 `_Fill`  
 使用做為空格的字元。  
  
 ` val`  
 要輸出的布林值類型或數目。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器所產生的位址超過最後一個項目的其中一個位置。  
  
### <a name="remarks"></a>備註  
 第一個受保護的虛擬成員函式會產生連續的項目開始 ` next` 產生整數輸出欄位的值從 ` val`。 函數會傳回迭代器指定的下一個位置插入項目產生的整數輸出欄位之外。  
  
 列印函式用於產生一系列的相同規則所產生的整數輸出欄位 `char` 檔案的項目。 每個這類字元項目會對應至對等項目類型的假設 **CharType** 簡單的一對一對應。 列印函式會填補的欄位，以空格或數字 0，不過，其中 `do_put` 會改為使用 **填滿**。 對等的列印轉換規格的決定方式如下︰  
  
-   如果 **iosbase**。 [旗標](../standard-library/ios-base-class.md#ios_base__flags) & `ios_base::basefield` == `ios_base::`[年 10 月](../Topic/%3Cios%3E%20functions.md#oct), ，轉換規格的 **lo**。  
  
-   如果 **iosbase.flags** & **ios_base::basefield** == `ios_base::`[十六進位](../Topic/%3Cios%3E%20functions.md#hex), ，轉換規格的 **lx**。  
  
-   否則，就是轉換規格 **ld**。  
  
 如果 **iosbase**。 [寬度](../standard-library/ios-base-class.md#ios_base__width) 為非零值，這個值的欄位寬度前面加上。 然後呼叫函式 **iosbase**。 **寬度**重欄位寬度設為零 (0)。  
  
 填補時才會發生的最小元素數目 *N* 必須指定的輸出欄位小於 **iosbase**。 [寬度](../standard-library/ios-base-class.md#ios_base__width)。 此類填補包含一連串的 *N* – **寬度** 複製的 **填滿**。 然後填補就會發生，如下所示︰  
  
-   如果 **iosbase**。 **旗標** & `ios_base::adjustfield` == `ios_base::`[左](../Topic/%3Cios%3E%20functions.md#left), ，旗標 **–** 前面加上。 （填補發生之後產生的文字）。  
  
-   如果 **iosbase.flags** & **ios_base::adjustfield** == `ios_base::`[內部](../Topic/%3Cios%3E%20functions.md#internal), ，旗標 **0** 前面加上。 （數字的輸出欄位填補進行列印函式填補 0 的位置）。  
  
-   否則，為前面加不上任何其他旗標。 （填補進行之前產生的順序）。  
  
 最後︰  
  
-   如果 **iosbase**。 **旗標** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) 為非零值，此旗標 **+** 前面加上的轉換規格。  
  
-   如果 **iosbase**。 **旗標** & **ios_base::**[showbase](../Topic/%3Cios%3E%20functions.md#showbase) 為非零值，此旗標 **#** 前面加上的轉換規格。  
  
 從整數格式輸出欄位進一步由 [地區設定 facet](../standard-library/locale-class.md#facet_class)**fac** 呼叫所傳回 [use_facet](../Topic/%3Clocale%3E%20functions.md#use_facet) < [numpunct](../standard-library/numpunct-class.md)\< **Elem**> ( **iosbase**。 [getloc](../standard-library/ios-base-class.md#ios_base__getloc))。 尤其是：  
  
- **fac**。 [群組](../standard-library/numpunct-class.md#numpunct__grouping) 決定小數點左邊數字的分組方式  
  
- **fac**。 [thousands_sep](../standard-library/numpunct-class.md#numpunct__thousands_sep) 決定分隔小數點左邊數字群組的順序  
  
 如果沒有群組條件約束所加諸 **fac**。 **群組** （其第一個項目具有值 CHAR_MAX），然後的執行個體 **fac**。 `thousands_sep` 會產生的輸出欄位。 否則，列印轉換發生後，會插入分隔符號。  
  
 第二個的受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    unsigned long val) const;
```  
  
 不同之處在於它會取代轉換規格的行為與第一個相同 **ld** 與 **lu**。  
  
 第三個受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    double val) const;
```  
  
 行為與第一個相同，不同之處在於它會產生浮點數的輸出欄位的值從 **val**。 **fac**。 [decimal_point](../standard-library/numpunct-class.md#numpunct__decimal_point) 分隔整數位數與小數位數的順序決定。 對等的列印轉換規格的決定方式如下︰  
  
-   如果 **iosbase**。 **旗標** & `ios_base::floatfield` == `ios_base::`[固定](../Topic/%3Cios%3E%20functions.md#fixed), ，轉換規格的 **lf**。  
  
-   如果 **iosbase**。 **旗標** & **ios_base::floatfield** == `ios_base::`[科學](../Topic/%3Cios%3E%20functions.md#scientific), ，轉換規格的 `le`。 如果 **iosbase**。 **旗標** & `ios_base::`[大寫](../Topic/%3Cios%3E%20functions.md#uppercase) 是零， **e** 會取代 **E**。  
  
-   否則，就是轉換規格 **lg**。 如果 **iosbase**。 **旗標** & **ios_base::uppercase** 是零， **g** 會取代 **G**。  
  
 如果 **iosbase**。 **旗標** & **ios_base::fixed** 為非零值或 **iosbase**。 [有效位數](../standard-library/ios-base-class.md#ios_base__precision) 大於有效位數的值是零， **iosbase**。 **有效位數** 前面加上的轉換規格。 任何填補的行為會與整數輸出欄位相同。 填補字元是 **填滿**。 最後︰  
  
-   如果 **iosbase**。 **旗標** & `ios_base::`[showpos](../Topic/%3Cios%3E%20functions.md#showpos) 為非零值，此旗標 **+** 前面加上的轉換規格。  
  
-   如果 **iosbase**。 **旗標** & `ios_base::`[showpoint](../Topic/%3Cios%3E%20functions.md#showpoint) 為非零值，此旗標 **#** 前面加上的轉換規格。  
  
 第四個的受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    long double val) const;
```  
  
 第三個不同處在於的行為相同限定詞 **l** 在轉換規格會取代 **L**。  
  
 第五個的受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    const void* val) const;
```  
  
 行為相同第一個轉換規格的差異在於 `p`**,，** 再加上任何需要指定填補的限定詞。  
  
 第六個的受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& _Iosbase,  
    CharType _Fill,
    bool val) const;
```  
  
 行為與第一個相同，不同之處在於它會產生布林值的輸出欄位從 ` val`。  
  
 布林值的輸出欄位會有兩種形式。 如果 **iosbase**。 **旗標** & `ios_base::`[boolalpha](../Topic/%3Cios%3E%20functions.md#boolalpha) 是 **false**, ，成員函式傳回 `do_put`(_ *下一步*, ，\_ *Iosbase*, ，\_ *填滿*, ，( **長**) ` val`)，這通常會產生 0 產生的順序 (如 **false**) 或 1 (如 **true**)。 否則，產生的序列可能是 **fac**。 [falsename](../standard-library/numpunct-class.md#numpunct__falsename)`)` (如 **false**)，或 **fac**。 [truename](../standard-library/numpunct-class.md#numpunct__truename) (如 **true**)。  
  
 第七個的受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    long long val) const;
```  
  
 不同之處在於它會取代轉換規格的行為與第一個相同 **ld** 與 **lld**。  
  
 第八個受保護的虛擬成員函式︰  
  
```  
virtual iter_type do_put(iter_type next,
    ios_base& iosbase,  
    Elem fill,
    unsigned long long val) const;
```  
  
 行為與第一個相同，不同之處在於它會取代轉換規格的 `ld` 與 `llu`。  
  
### <a name="example"></a>範例  
  請參閱範例 [放](#num_put__put), ，而它會呼叫 `do_put`。  
  
##  <a name="a-namenumputitertypea-numputitertype"></a><a name="num_put__iter_type"></a>  num_put:: iter_type  
 描述輸出迭代器的類型。  
  
```  
typedef OutputIterator iter_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **OutputIterator。**  
  
##  <a name="a-namenumputnumputa-numputnumput"></a><a name="num_put__num_put"></a>  num_put:: num_put  
 `num_put` 類型物件的建構函式。  
  
```  
explicit num_put(size_t _Refs = 0);
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
  
 建構函式初始化具有其基底物件 **地區設定::**[facet](../standard-library/locale-class.md#facet_class)(_ *Refs*)。  
  
##  <a name="a-namenumputputa-numputput"></a><a name="num_put__put"></a>  num_put:: put  
 將數字轉換成一系列 **CharType**表示數字格式化為特定地區設定。  
  
```  
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    bool val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    unsigned long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Long long val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    Unsigned long long val) const;

 
 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    long double val) const;

 
iter_type put(
    iter_type dest,  
    ios_base& _Iosbase,  
    _Elem _Fill,  
    const void* val) const;
```  
  
### <a name="parameters"></a>參數  
 ` dest`  
 迭代器定址插入字串的第一個元素中。  
  
 `_Iosbase`  
 指定包含與用來插入的輸出和格式化輸出的旗標 numpunct facet 的地區設定的資料流。  
  
 `_Fill`  
 使用做為空格的字元。  
  
 ` val`  
 要輸出的布林值類型或數目。  
  
### <a name="return-value"></a>傳回值  
 輸出迭代器所產生的位址超過最後一個項目的其中一個位置。  
  
### <a name="remarks"></a>備註  
 所有成員函式會都傳回 [do_put](#num_put__do_put)( ` next`, ，`_Iosbase`, ，`_Fill`, ，` val`)。  
  
### <a name="example"></a>範例  
  
```  
// num_put_put.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
#include <sstream>  
using namespace std;  
int main( )  
{  
   locale loc( "german_germany" );  
   basic_stringstream<char> psz2;  
   ios_base::iostate st = 0;  
   long double fVal;  
   cout << "The thousands separator is: "   
        << use_facet < numpunct <char> >(loc).thousands_sep( )   
        << endl;  
  
   psz2.imbue( loc );  
   use_facet < num_put < char > >  
      ( loc ).put(basic_ostream<char>::_Iter(psz2.rdbuf( ) ),  
                    psz2, ' ', fVal=1000.67);  
  
   if ( st & ios_base::failbit )  
      cout << "num_put( ) FAILED" << endl;  
   else  
      cout << "num_put( ) = " << psz2.rdbuf( )->str( ) << endl;  
}  
```  
  
```Output  
The thousands separator is: .  
num_put( ) = 1.000,67  
```  
  
## <a name="see-also"></a>另請參閱  
 [\< 地區設定>](../standard-library/locale.md)   
 [facet 類別](../standard-library/locale-class.md#facet_class)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

