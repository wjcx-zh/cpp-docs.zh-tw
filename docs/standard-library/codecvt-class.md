---
title: "codecvt 類別 | Microsoft Docs"
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
  - "codecvt"
  - "std::codecvt"
  - "std.codecvt"
  - "xlocale/std::codecvt"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "codecvt 類別"
ms.assetid: 37d3efa1-2b7f-42b6-b04f-7a972c8c2c86
caps.latest.revision: 23
caps.handback.revision: 23
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# codecvt 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

樣板類別，描述可做為地區設定 facet 的物件。 它可以控制程式內部字元編碼的值序列和程式外部字元編碼的值序列之間的轉換。  
  
## <a name="syntax"></a>語法  
  
```  
template <class CharType, class Byte, class StateType>  
class codecvt : public locale::facet, codecvt_base;  
```  
  
#### <a name="parameters"></a>參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
 `Byte`  
 用於程式外部字元編碼的類型。  
  
 `StateType`  
 類型，可以用來表示字元表示的內部和外部類型之間的轉換中繼狀態。  
  
## <a name="remarks"></a>備註  
 此樣板類別描述可以做為物件 [地區設定 facet](../standard-library/locale-class.md#facet_class), ，以控制類型的值序列之間轉換 `CharType` 類型的值序列和 `Byte`。 類別 `StateType` 表示轉換特性，而類別 `StateType` 的物件儲存轉換期間任何必要的狀態資訊。  
  
 內部編碼使用表示搭配每個字元固定的位元組數，通常是 `char` 類型或 `wchar_t` 類型。  
  
 如同所有地區設定 facet，靜態物件 `id` 有初始儲存值零。 第一次嘗試存取它的儲存的值儲存在唯一的正值 `id`。  
  
 範本版本 [do_in](#codecvt__do_in) 和 [do_out](#codecvt__do_out) 一律會傳回 `codecvt_base::noconv`。  
  
 Standard C++ 程式庫定義數個明確特製化：  
  
 `template<>`  
  
 `codecvt<wchar_t, char, mbstate_t>`  
  
 在 `wchar_t` 和 `char` 序列之間轉換。  
  
 `template<>`  
  
 `codecvt<char16_t, char, mbstate_t>`  
  
 在編碼為 UTF-16 的 `char16_t` 序列和編碼為 UTF-8 的 `char` 序列之間轉換。  
  
 `template<>`  
  
 `codecvt<char32_t, char, mbstate_t>`  
  
 在編碼為 UTF-32 (UCS-4) 的 `char32_t` 序列和編碼為 UTF-8 的 `char` 序列之間轉換。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[codecvt](#codecvt__codecvt)|做為地區設定 facet 處理轉換之 `codecvt` 類別物件的建構函式。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[extern_type](#codecvt__extern_type)|用於外部表示的字元類型。|  
|[intern_type](#codecvt__intern_type)|用於內部表示的字元類型。|  
|[state_type](#codecvt__state_type)|字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[always_noconv](#codecvt__always_noconv)|測試是否不需要完成轉換。|  
|[do_always_noconv](#codecvt__do_always_noconv)|虛擬函式，呼叫以測試是否不需要完成轉換。|  
|[do_encoding](#codecvt__do_encoding)|虛擬函式，測試 `Byte` 資料流的編碼方式是否為狀態相關，所用的 `Byte` 和所產生的 `CharType` 之間的比率是否為常數，而且，如果是的話，判斷該比率的值。|  
|[do_in](#codecvt__do_in)|虛擬函式，呼叫以將內部 `Byte` 序列轉換為外部 `CharType` 序列。|  
|[do_length](#codecvt__do_length)|虛擬函式，判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。|  
|[do_max_length](#codecvt__do_max_length)|虛擬函式，傳回產生一個內部 `CharType` 所需的外部 Byte 數目上限。|  
|[do_out](#codecvt__do_out)|虛擬函式，呼叫以將內部 `CharType` 序列轉換為外部 Byte 序列。|  
|[do_unshift](#codecvt__do_unshift)|虛擬函式，呼叫以提供狀態相關轉換所需的 `Byte`，以完成 `Byte` 序列的最後一個字元。|  
|[編碼方式](#codecvt__encoding)|測試 `Byte` 資料流的編碼方式是否為狀態相關，所用的 `Byte` 和所產生的 `CharType` 之間的比率是否為常數，而且，如果是的話，判斷該比率的值。|  
|[在](#codecvt__in)|將 `Byte` 序列的外部表示轉換為 `CharType` 序列的內部表示。|  
|[長度](#codecvt__length)|判斷外部 `Byte` 指定的序列有多少個 `Byte` 產生不超過指定的內部 `CharType` 數目，並傳回 `Byte` 的數字。|  
|[max_length](#codecvt__max_length)|傳回產生一個內部 `Byte` 所需的外部 `CharType` 數目上限。|  
|[向外](#codecvt__out)|將內部 `CharType` 序列轉換為外部 `Byte` 序列。|  
|[unshift](#codecvt__unshift)|提供狀態相關轉換所需的 `Byte`，以完成 `Byte` 序列的最後一個字元。|  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間：** std  
  
##  <a name="a-namecodecvtalwaysnoconva-codecvtalwaysnoconv"></a><a name="codecvt__always_noconv"></a>  codecvt:: always_noconv  
 測試是否不需要完成轉換。  
  
```  
bool always_noconv() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 布林值，是 **true** 如果需要不執行任何轉換; **false** 是至少一個需要執行的動作。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_always_noconv](#codecvt__do_always_noconv)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_always_noconv.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   bool result1 = use_facet<codecvt<char, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result1 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
  
   bool result2 = use_facet<codecvt<wchar_t, char, mbstate_t> >   
      ( loc ).always_noconv( );  
  
   if ( result2 )  
      cout << "No conversion is needed." << endl;  
   else  
      cout << "At least one conversion is required." << endl;  
}  
```  
  
```Output  
No conversion is needed.  
At least one conversion is required.  
```  
  
##  <a name="a-namecodecvtcodecvta-codecvtcodecvt"></a><a name="codecvt__codecvt"></a>  codecvt:: codecvt  
 針對類別 codecvt 做為地區設定 facet 處理轉換的物件建構函式。  
  
```  
explicit codecvt(size_t _Refs = 0);
```  
  
### <a name="parameters"></a>參數  
 `_Refs`  
 用來指定物件的記憶體管理類型的整數值。  
  
### <a name="remarks"></a>備註  
 可能值 `_Refs` 參數和其重要性為︰  
  
-   0︰ 物件存留期由包含它的地區設定。  
  
-   1︰ 必須以手動方式管理物件存留期。  
  
-   \> 0︰ 未定義這些值。  
  
 建構函式會初始化其 `locale::facet` 與基底物件 **地區設定::**[facet](../standard-library/locale-class.md#facet_class)( `_Refs`) *。*  
  
##  <a name="a-namecodecvtdoalwaysnoconva-codecvtdoalwaysnoconv"></a><a name="codecvt__do_always_noconv"></a>  codecvt:: do_always_noconv  
 虛擬函式，呼叫以測試是否不需要完成轉換。  
  
```  
virtual bool do_always_noconv() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 受保護的虛擬成員函式會傳回 **true** 才每次呼叫 [do_in](#codecvt__do_in) 或 [do_out](#codecvt__do_out) 傳回 **noconv**。  
  
 範本版本永遠傳回 **true**。  
  
### <a name="example"></a>範例  
  請參閱範例 [always_noconv](#codecvt__always_noconv), ，而它會呼叫 `do_always_noconv`。  
  
##  <a name="a-namecodecvtdoencodinga-codecvtdoencoding"></a><a name="codecvt__do_encoding"></a>  codecvt:: do_encoding  
 如果測試的虛擬函式的編碼方式 **位元組** 資料流是否為狀態相關，之間的比率 **位元組**用和 **CharType**產生會為常數，而且如果是的話，判斷該比率的值。  
  
```  
virtual int do_encoding() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 受保護的虛擬成員函式會傳回︰  
  
-   – 1，如果編碼方式類型序列 `extern_type` 所相依的狀態。  
  
-   0，如果編碼方式涉及不同長度的序列。  
  
- *N*, ，如果編碼方式牽涉到只有序列的長度 *N*  
  
### <a name="example"></a>範例  
  請參閱範例 [編碼](#codecvt__encoding), ，而它會呼叫 `do_encoding`。  
  
##  <a name="a-namecodecvtdoina-codecvtdoin"></a><a name="codecvt__do_in"></a>  codecvt:: do_in  
 虛擬函式，呼叫以將轉換為外部 **位元組**的內部序列 **CharType**s。  
  
```  
virtual result do_in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 要轉換的序列開頭的指標。  
  
 ` last1`  
 要轉換的序列結尾指標。  
  
 ` next1`  
 轉換序列，第一個未轉換字元結尾之外的指標。  
  
 ` first2`  
 已轉換的序列開頭的指標。  
  
 ` last2`  
 已轉換的序列結尾指標。  
  
 ` next2`  
 指標 **CharType** 這是最後一個轉換後 **CharType**, ，目標序列中的第一個未經過更改的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回指出成功、 部分成功或作業失敗。 此函數會傳回︰  
  
- **codecvt_base::error** 如果來源序列是不良的格式。  
  
- `codecvt_base::noconv` 如果函式會執行任何轉換。  
  
- **codecvt_base::ok** 如果轉換成功。  
  
- **codecvt_base::partial** 如果沒有足夠的來源或目的地不是不夠大，才能成功轉換。  
  
### <a name="remarks"></a>備註  
 `_State` 必須呈現新的來源序列的開頭初始轉換狀態。 視需要以反映目前狀態的轉換成功，函式會改變它的儲存的值。 處於未指定它的儲存的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [中](#codecvt__in), ，而它會呼叫 `do_in`。  
  
##  <a name="a-namecodecvtdolengtha-codecvtdolength"></a><a name="codecvt__do_length"></a>  codecvt:: do_length  
 虛擬函式，可決定多少 **位元組**指定序列的外部 **位元組**產生不超過指定數目的內部 **CharType**s，並傳回該數目的 **位元組**s。  
  
```  
virtual int do_length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 外部序列開頭的指標。  
  
 ` last1`  
 外部序列結尾指標。  
  
 `_Len2`  
 最大數目 **位元組**s 可傳回由成員函式。  
  
### <a name="return-value"></a>傳回值  
 整數，表示轉換不大於最大數目的計數 `_Len2`, 、 由外部來源順序定義 [ ` first1`, ，` last1`)。  
  
### <a name="remarks"></a>備註  
 有效率地呼叫受保護的虛擬成員函式 `do_in`( `_State`, ，` first1`, ，` last1`, ，` next1`, ，`_Buf`, ，`_Buf` + `_Len2`, ，` next2`) 的 `_State` （狀態的複本），有些緩衝 `_Buf`, ，與指標 ` next1`和 ` next2`。  
  
 它接著會傳回 ` next2` – **buf**。 因此，它會計算的轉換不大於上限 `_Len2`, ，定義來源順序，在 [ ` first1`, ，` last1`)。  
  
 範本版本永遠傳回較小的 ` last1` – ` first1` 和 `_Len2`。  
  
### <a name="example"></a>範例  
  請參閱範例 [長度](#codecvt__length), ，而它會呼叫 **do_length**。  
  
##  <a name="a-namecodecvtdomaxlengtha-codecvtdomaxlength"></a><a name="codecvt__do_max_length"></a>  codecvt:: do_max_length  
 虛擬函式會傳回最大的外部 **位元組**產生一個內部所需 **CharType**。  
  
```  
virtual int do_max_length() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 最大數目 **位元組**產生一個所需 **CharType**。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式會傳回可傳回的最大允許值 [do_length](#codecvt__do_length)( ` first1`, ，` last1`, ，1) 的任意有效值 ` first1` 和 ` last1`。  
  
### <a name="example"></a>範例  
  請參閱範例 [max_length](#codecvt__max_length), ，而它會呼叫 `do_max_length`。  
  
##  <a name="a-namecodecvtdoouta-codecvtdoout"></a><a name="codecvt__do_out"></a>  codecvt:: do_out  
 虛擬函式，呼叫以將轉換的內部序列 **CharType**序列轉換為外部 **位元組**s。  
  
```  
virtual result do_out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 要轉換的序列開頭的指標。  
  
 ` last1`  
 要轉換的序列結尾指標。  
  
 ` next1`  
 第一個指標參考不轉換 **CharType**, ，最後一個之後 **CharType** 轉換。  
  
 ` first2`  
 已轉換的序列開頭的指標。  
  
 ` last2`  
 已轉換的序列結尾指標。  
  
 ` next2`  
 第一個指標參考不轉換 **位元組**, ，最後一個之後 **位元組** 轉換。  
  
### <a name="return-value"></a>傳回值  
 此函數會傳回︰  
  
- **codecvt_base::error** 如果來源序列是不良的格式。  
  
- `codecvt_base::noconv` 如果函式會執行任何轉換。  
  
- **codecvt_base::ok** 如果轉換成功。  
  
- **codecvt_base::partial** 如果沒有足夠的來源或目的地不是夠大，才能成功轉換。  
  
### <a name="remarks"></a>備註  
 `_State` 必須呈現新的來源序列的開頭初始轉換狀態。 視需要以反映目前狀態的轉換成功，函式會改變它的儲存的值。 處於未指定它的儲存的值。  
  
### <a name="example"></a>範例  
  請參閱範例 [出](#codecvt__out), ，而它會呼叫 `do_out`。  
  
##  <a name="a-namecodecvtdounshifta-codecvtdounshift"></a><a name="codecvt__do_unshift"></a>  codecvt:: do_unshift  
 虛擬函式，呼叫以提供 **位元組**狀態相關轉換所需完成一系列的最後一個字元 **位元組**s。  
  
```  
virtual result do_unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first2`  
 在目的範圍中的第一個位置的指標。  
  
 ` last2`  
 在目的範圍中最後一個位置的指標。  
  
 ` next2`  
 第一個未改變序列中項目的指標。  
  
### <a name="return-value"></a>傳回值  
 此函數會傳回︰  
  
- **codecvt_base::error** 如果 _ *狀態* 代表無效的狀態  
  
- `codecvt_base::noconv` 如果函式會執行任何轉換  
  
- **codecvt_base::ok** 如果轉換成功  
  
- **codecvt_base::partial** 如果目的地無法夠大，才能成功轉換  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式會嘗試將轉換的來源項目 **CharType**(0)，它會儲存在目的地序列 [ ` first2`, ，` last2`)，終止的項目除外 **位元組**(0)。 它永遠都會儲存在 ` next2` 目的地序列中第一個未改變的項目之指標。  
  
 _ *狀態* 必須呈現新的來源序列開頭的初始轉換狀態。 視需要以反映目前狀態的轉換成功，函式會改變它的儲存的值。 一般而言，轉換的來源項目 **CharType**(0) 的初始轉換狀態中離開目前的狀態。  
  
### <a name="example"></a>範例  
  請參閱範例 [unshift](#codecvt__unshift), ，而它會呼叫 `do_unshift`。  
  
##  <a name="a-namecodecvtencodinga-codecvtencoding"></a><a name="codecvt__encoding"></a>  codecvt:: encoding  
 如果測試的編碼方式 **位元組** 資料流是否為狀態相關，之間的比率 **位元組**用和 **CharType**產生為常數，而且，如果是的話，判斷該比率的值。  
  
```  
int encoding() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 如果傳回值為正數，則這個值會比固定數目的 **位元組** 來產生所需字元 **CharType** 字元。  
  
 受保護的虛擬成員函式會傳回︰  
  
-   – 1，如果編碼方式類型序列 `extern_type` 所相依的狀態。  
  
-   0，如果編碼方式涉及不同長度的序列。  
  
- *N*, ，如果編碼方式牽涉到只有序列的長度 *n。*  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_encoding](#codecvt__do_encoding)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_encoding.cpp  
// compile with: /EHsc  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc ( "German_Germany" );  
   int result1 = use_facet<codecvt<char, char, mbstate_t> > ( loc ).encoding ( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<wchar_t, char, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
   result1 = use_facet<codecvt<char, wchar_t, mbstate_t> > ( loc ).encoding( );  
   cout << result1 << endl;  
}  
```  
  
```Output  
1  
1  
1  
```  
  
##  <a name="a-namecodecvtexterntypea-codecvtexterntype"></a><a name="codecvt__extern_type"></a>  codecvt:: extern_type  
 用於外部表示的字元類型。  
  
```  
typedef Byte extern_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **位元組**。  
  
##  <a name="a-namecodecvtina-codecvtin"></a><a name="codecvt__in"></a>  codecvt:: in  
 將序列的外部表示法 **位元組**一連串的內部表示 **CharType**s。  
  
```  
result in(
    StateType& _State,  
    const Byte* first1,   
    const Byte* last1,   
    const Byte*& next1,  
    CharType* first2,  
    CharType* last2,  
    CharType*& next2,) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 要轉換的序列開頭的指標。  
  
 ` last1`  
 要轉換的序列結尾指標。  
  
 ` next1`  
 超過已轉換的第一個未轉換的字元序列的結尾的指標。  
  
 ` first2`  
 已轉換的序列開頭的指標。  
  
 ` last2`  
 已轉換的序列結尾指標。  
  
 ` next2`  
 指標 **CharType** 這是最後一個轉換後 **Chartype** 目的地序列中的第一個未經過更改的字元。  
  
### <a name="return-value"></a>傳回值  
 傳回表示成功，只有一部分成功或失敗的作業。 此函數會傳回︰  
  
- **codecvt_base::error** 如果來源序列是不良的格式。  
  
- `codecvt_base::noconv` 如果函式會執行任何轉換。  
  
- **codecvt_base::ok** 如果轉換成功。  
  
- **codecvt_base::partial** 如果沒有足夠的來源或目的地不是夠大，才能成功轉換。  
  
### <a name="remarks"></a>備註  
 `_State` 必須呈現新的來源序列的開頭初始轉換狀態。 函式會改變它的儲存的值，如有需要以反映目前狀態的轉換成功。 部分在轉換之後， `_State` 必須設定以允許繼續新字元到達時轉換。  
  
 成員函式傳回 [do_in](#codecvt__do_in)( `_State`, ，_ *First1 last1、 next1，First2，_Llast2，next2*)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_in.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string to be converted!";  
   wchar_t pwszInt [LEN+1];  
   memset(&pwszInt[0], 0, (sizeof(wchar_t))*(LEN+1));  
   const char* pszNext;  
   wchar_t* pwszNext;  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).in( state,  
          pszExt, &pszExt[strlen(pszExt)], pszNext,  
          pwszInt, &pwszInt[strlen(pszExt)], pwszNext );  
   pwszInt[strlen(pszExt)] = 0;  
   wcout << ( (res!=codecvt_base::error)  L"It worked! " : L"It didn't work! " )  
   << L"The converted string is:\n ["  
   << &pwszInt[0]  
   << L"]" << endl;  
   exit(-1);  
}  
```  
  
```Output  
It worked! The converted string is:  
 [This is the string to be converted!]  
```  
  
##  <a name="a-namecodecvtinterntypea-codecvtinterntype"></a><a name="codecvt__intern_type"></a>  codecvt:: intern_type  
 用於內部表示的字元類型。  
  
```  
typedef CharType intern_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **CharType**。  
  
##  <a name="a-namecodecvtlengtha-codecvtlength"></a><a name="codecvt__length"></a>  codecvt:: length  
 判斷多少 **位元組**指定序列的外部 **位元組**產生不超過指定數目的內部 **CharType**s，並傳回該數目的 **位元組**s。  
  
```  
int length(
    const StateType& _State,  
    const Byte* first1,   
    const Byte* last1,  
    size_t _Len2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 外部序列開頭的指標。  
  
 ` last1`  
 外部序列結尾指標。  
  
 `_Len2`  
 成員函式傳回的位元組數目上限。  
  
### <a name="return-value"></a>傳回值  
 整數，表示轉換不大於最大數目的計數 `_Len2`, 、 由外部來源順序定義 [ ` first1`, ，` last1`)。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_length](#codecvt__do_length)( *_State，first1*, ，` last1`, ，`_Len2`)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char* pszExt = "This is the string whose length is to be measured!";  
   mbstate_t state = {0};  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
     ( loc ).length( state,  
          pszExt, &pszExt[strlen(pszExt)], LEN );  
   cout << "The length of the string is: ";  
   wcout << res;  
   cout << "." << endl;  
   exit(-1);  
}  
```  
  
```Output  
The length of the string is: 50.  
```  
  
##  <a name="a-namecodecvtmaxlengtha-codecvtmaxlength"></a><a name="codecvt__max_length"></a>  codecvt:: max_length  
 傳回最大數目為外部 **位元組**產生一個內部所需 **CharType**。  
  
```  
int max_length() const throw();
```  
  
### <a name="return-value"></a>傳回值  
 最大數目 **位元組**產生一個所需 **CharType**。  
  
### <a name="remarks"></a>備註  
 成員函式傳回 [do_max_length](#codecvt__do_max_length)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_max_length.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
using namespace std;  
  
int main( )     
{  
   locale loc( "C");//English_Britain" );//German_Germany  
   int res = use_facet<codecvt<char, char, mbstate_t> >  
     ( loc ).max_length( );  
   wcout << res << endl;  
}  
```  
  
```Output  
1  
```  
  
##  <a name="a-namecodecvtouta-codecvtout"></a><a name="codecvt__out"></a>  codecvt:: out  
 將內部序列轉換 **CharType**序列轉換為外部 **位元組**s。  
  
```  
result out(
    StateType& _State,  
    const CharType* first1,   
    const CharType* last1,  
    const CharType*& next1,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first1`  
 要轉換的序列開頭的指標。  
  
 ` last1`  
 要轉換的序列結尾指標。  
  
 ` next1`  
 第一個指標參考不轉換 **CharType** 最後一個之後 **CharType** 轉換。  
  
 ` first2`  
 已轉換的序列開頭的指標。  
  
 ` last2`  
 已轉換的序列結尾指標。  
  
 ` next2`  
 第一個指標參考不轉換 **位元組** 上次轉換之後 **位元組**。  
  
### <a name="return-value"></a>傳回值  
 成員函式傳回 [do_out](#codecvt__do_out)( `_State`, ，` first1`, ，` last1`, ，` next1`, ，` first2`, ，` last2`, ，` next2`)。  
  
### <a name="remarks"></a>備註  
 如需詳細資訊，請參閱 [codecvt:: do_out](#codecvt__do_out)。  
  
### <a name="example"></a>範例  
  
```  
// codecvt_out.cpp  
// compile with: /EHsc  
#define _INTL  
#include <locale>  
#include <iostream>  
#include <wchar.h>  
using namespace std;  
#define LEN 90  
int main( )     
{  
   char pszExt[LEN+1];  
   wchar_t *pwszInt = L"This is the wchar_t string to be converted.";  
   memset( &pszExt[0], 0, ( sizeof( char ) )*( LEN+1 ) );  
   char* pszNext;  
   const wchar_t* pwszNext;  
   mbstate_t state;  
   locale loc("C");//English_Britain");//German_Germany  
   int res = use_facet<codecvt<wchar_t, char, mbstate_t> >  
      ( loc ).out( state,  
      pwszInt, &pwszInt[wcslen( pwszInt )], pwszNext ,  
      pszExt, &pszExt[wcslen( pwszInt )], pszNext );  
   pszExt[wcslen( pwszInt )] = 0;  
   cout << ( ( res!=codecvt_base::error )  "It worked: " : "It didn't work: " )  
   << "The converted string is:\n ["  
   << &pszExt[0]  
   << "]" << endl;  
}  
```  
  
```Output  
It worked: The converted string is:  
 [This is the wchar_t string to be converted.]  
```  
  
##  <a name="a-namecodecvtstatetypea-codecvtstatetype"></a><a name="codecvt__state_type"></a>  codecvt:: state_type  
 字元類型，用來表示內部和外部表示之間轉換期間的中繼狀態。  
  
```  
typedef StateType state_type;  
```  
  
### <a name="remarks"></a>備註  
 型別是範本參數的同義字 **StateType**。  
  
##  <a name="a-namecodecvtunshifta-codecvtunshift"></a><a name="codecvt__unshift"></a>  codecvt:: unshift  
 提供 **位元組**狀態相關轉換所需完成一系列的最後一個字元 **位元組**s。  
  
```  
result unshift(
    StateType& _State,  
    Byte* first2,   
    Byte* last2,   
    Byte*& next2) const;
```  
  
### <a name="parameters"></a>參數  
 `_State`  
 成員函式的呼叫之間不會保留，轉換狀態。  
  
 ` first2`  
 在目的範圍中的第一個位置的指標。  
  
 ` last2`  
 在目的範圍中最後一個位置的指標。  
  
 ` next2`  
 第一個未改變序列中項目的指標。  
  
### <a name="return-value"></a>傳回值  
 此函數會傳回︰  
  
- **codecvt_base::error** 如果狀態表示無效的狀態。  
  
- `codecvt_base::noconv` 如果函式會執行任何轉換。  
  
- **codecvt_base::ok** 如果轉換成功。  
  
- **codecvt_base::partial** 如果目的地無法夠大，才能成功轉換。  
  
### <a name="remarks"></a>備註  
 受保護的虛擬成員函式會嘗試將轉換的來源項目 **CharType**(0)，它會儲存在目的地序列 [ ` first2`, ，` last2`)，終止的項目除外 **位元組**(0)。 它永遠都會儲存在 ` next2` 目的地序列中第一個未改變的項目之指標。  
  
 `_State` 必須呈現新的來源序列的開頭初始轉換狀態。 函式會改變它的儲存的值，如有需要以反映目前狀態的轉換成功。 一般而言，轉換的來源項目 **CharType**(0) 的初始轉換狀態中離開目前的狀態。  
  
 成員函式傳回 [do_unshift](#codecvt__do_unshift)( `_State`, ，` first2`, ，` last2`, ，` next2` )。  
  
## <a name="see-also"></a>另請參閱  
 [\< 地區設定>](../standard-library/locale.md)   
 [字碼頁](../c-runtime-library/code-pages.md)   
 [地區設定名稱、 語言和國家/地區字串](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

