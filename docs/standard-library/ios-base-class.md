---
title: "ios_base 類別 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- xiosbase/std::ios_base
- ios/std::ios_base::event_callback
- xiosbase/std::ios_base::fmtflags
- xiosbase/std::ios_base::iostate
- xiosbase/std::ios_base::openmode
- xiosbase/std::ios_base::seekdir
- xiosbase/std::ios_base::event
- xiosbase/std::ios_base::adjustfield
- xiosbase/std::ios_base::app
- xiosbase/std::ios_base::ate
- xiosbase/std::ios_base::badbit
- xiosbase/std::ios_base::basefield
- xiosbase/std::ios_base::beg
- xiosbase/std::ios_base::binary
- xiosbase/std::ios_base::boolalpha
- xiosbase/std::ios_base::cur
- xiosbase/std::ios_base::dec
- xiosbase/std::ios_base::end
- xiosbase/std::ios_base::eofbit
- xiosbase/std::ios_base::failbit
- xiosbase/std::ios_base::fixed
- xiosbase/std::ios_base::floatfield
- xiosbase/std::ios_base::goodbit
- xiosbase/std::ios_base::hex
- xiosbase/std::ios_base::in
- xiosbase/std::ios_base::internal
- xiosbase/std::ios_base::left
- xiosbase/std::ios_base::oct
- xiosbase/std::ios_base::out
- xiosbase/std::ios_base::right
- xiosbase/std::ios_base::scientific
- xiosbase/std::ios_base::showbase
- xiosbase/std::ios_base::showpoint
- xiosbase/std::ios_base::showpos
- xiosbase/std::ios_base::skipws
- xiosbase/std::ios_base::trunc
- xiosbase/std::ios_base::unitbuf
- xiosbase/std::ios_base::uppercase
- xiosbase/std::ios_base::failure
- xiosbase/std::ios_base::flags
- xiosbase/std::ios_base::getloc
- xiosbase/std::ios_base::imbue
- xiosbase/std::ios_base::Init
- xiosbase/std::ios_base::iword
- xiosbase/std::ios_base::precision
- xiosbase/std::ios_base::pword
- ios/std::ios_base::register_callback
- xiosbase/std::ios_base::setf
- xiosbase/std::ios_base::sync_with_stdio
- xiosbase/std::ios_base::unsetf
- xiosbase/std::ios_base::width
- xiosbase/std::ios_base::xalloc
dev_langs: C++
helpviewer_keywords:
- std::ios_base [C++]
- std::ios_base [C++], event_callback
- std::ios_base [C++], fmtflags
- std::ios_base [C++], iostate
- std::ios_base [C++], openmode
- std::ios_base [C++], seekdir
- std::ios_base [C++], event
- std::ios_base [C++], adjustfield
- std::ios_base [C++], app
- std::ios_base [C++], ate
- std::ios_base [C++], badbit
- std::ios_base [C++], basefield
- std::ios_base [C++], beg
- std::ios_base [C++], binary
- std::ios_base [C++], boolalpha
- std::ios_base [C++], cur
- std::ios_base [C++], dec
- std::ios_base [C++], end
- std::ios_base [C++], eofbit
- std::ios_base [C++], failbit
- std::ios_base [C++], fixed
- std::ios_base [C++], floatfield
- std::ios_base [C++], goodbit
- std::ios_base [C++], hex
- std::ios_base [C++], in
- std::ios_base [C++], internal
- std::ios_base [C++], left
- std::ios_base [C++], oct
- std::ios_base [C++], out
- std::ios_base [C++], right
- std::ios_base [C++], scientific
- std::ios_base [C++], showbase
- std::ios_base [C++], showpoint
- std::ios_base [C++], showpos
- std::ios_base [C++], skipws
- std::ios_base [C++], trunc
- std::ios_base [C++], unitbuf
- std::ios_base [C++], uppercase
- std::ios_base [C++], failure
- std::ios_base [C++], flags
- std::ios_base [C++], getloc
- std::ios_base [C++], imbue
- std::ios_base [C++], Init
- std::ios_base [C++], iword
- std::ios_base [C++], precision
- std::ios_base [C++], pword
- std::ios_base [C++], register_callback
- std::ios_base [C++], setf
- std::ios_base [C++], sync_with_stdio
- std::ios_base [C++], unsetf
- std::ios_base [C++], width
- std::ios_base [C++], xalloc
ms.assetid: 0f9e0abc-f70f-49bc-aa1f-003859f56cfe
caps.latest.revision: "21"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 04605ec5df5512549822d0e585bf1b28eb0b42e6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="iosbase-class"></a>ios_base 類別
此類別說明未依存於範本參數的輸入和輸出資料流通用的儲存體和成員函式。 (範本類別 [basic_ios](../standard-library/basic-ios-class.md) 描述通用且與範本參數相依的項目)。  
  
 Ios_base 類別的物件會儲存格式設定資訊，包括：  
  
-   [fmtflags](#fmtflags) 類型物件中的格式旗標。  
  
-   [iostate](#iostate) 類型物件中的例外狀況遮罩。  
  
-   類型的物件中的欄位寬度`int`。  
  
-   `int` 類型物件中的顯示精確度。  
  
-   **locale** 類型物件中的地區設定物件。  
  
-   兩個可延伸的陣列，具有 **long** 和 `void` 指標的元素。  
  
 ios_base 類別的物件會一併將資料流狀態資訊儲存在 [iostate](#iostate) 類型的物件中，以及儲存一個回呼堆疊。  
  
### <a name="constructors"></a>建構函式  
  
|||  
|-|-|  
|[ios_base](#ios_base)|建構 `ios_base` 物件。|  
  
### <a name="typedefs"></a>Typedefs  
  
|||  
|-|-|  
|[event_callback](#event_callback)|描述傳遞給 [register_call](#register_callback) 的函式。|  
|[fmtflags](#fmtflags)|指定輸出外觀的常數。|  
|[iostate](#iostate)|定義描述資料流狀態的常數。|  
|[openmode](#openmode)|描述如何與資料流互動。|  
|[seekdir](#seekdir)|指定位移作業的起點。|  
  
### <a name="enums"></a>列舉  
  
|||  
|-|-|  
|[event](#event)|指定事件類型。|  
  
### <a name="constants"></a>常數  
  
|||  
|-|-|  
|[adjustfield](#fmtflags)|一個以 `internal` &#124; `left` &#124; `right` 方式定義的位元遮罩。|  
|[app](#openmode)|指定在每次插入之前搜尋到資料流的結尾。|  
|[ate](#openmode)|指定在第一次建立控制物件時搜尋到資料流的結尾。|  
|[badbit](#iostate)|記錄資料流緩衝區的完整性遺失。|  
|[basefield](#fmtflags)|一個以 `dec` &#124; `hex` &#124; `oct` 方式定義的位元遮罩。|  
|[beg](#seekdir)|指定相對於序列開頭的搜尋。|  
|[binary](#openmode)|指定檔案應該以二進位資料流讀取，而不是文字資料流。|  
|[boolalpha](#fmtflags)|指定以名稱形式插入或擷取 `bool` 類型的物件 (例如 `true` 和 `false`)，而不是以數值形式。|  
|[cur](#seekdir)|指定相對於序列中目前位置的搜尋。|  
|[dec](#fmtflags)|指定以十進位格式插入或擷取整數值。|  
|[end](#seekdir)|指定相對於序列結尾的搜尋。|  
|[eofbit](#iostate)|從資料流擷取時記錄檔案結尾。|  
|[failbit](#iostate)|記錄從資料流擷取有效欄位失敗。|  
|[fixed](#fmtflags)|以固定點格式插入浮點數值 (沒有指數欄位)。|  
|[floatfield](#fmtflags)|一個以 `fixed` &#124; `scientific` 方式定義的位元遮罩|  
|[goodbit](#iostate)|清除所有狀態位元。|  
|[hex](#fmtflags)|指定以十六進位格式插入或擷取整數值。|  
|[in](#openmode)|指定從資料流擷取。|  
|[internal](#fmtflags)|藉由在產生的數字欄位內部一點中插入填滿字元，來填補欄位寬度。|  
|[left](#fmtflags)|指定左側對齊。|  
|[oct](#fmtflags)|指定以八進位格式插入或擷取整數值。|  
|[out](#openmode)|指定插入資料流。|  
|[right](#fmtflags)|指定右側對齊。|  
|[scientific](#fmtflags)|指定以科學記號格式插入浮點數值 (具有一個指數欄位)。|  
|[showbase](#fmtflags)|指定插入可顯示所產生整數欄位之基底的前置詞。|  
|[showpoint](#fmtflags)|指定在產生的浮點欄位無條件插入小數點。|  
|[showpos](#fmtflags)|指定在產生的非負數字欄位插入加號。|  
|[skipws](#fmtflags)|指定在進行某些擷取前，略過前置空白字元。|  
|[trunc](#openmode)|指定在控制物件建立時刪除現有檔案的內容。|  
|[unitbuf](#fmtflags)|導致在每次插入之後清除輸出。|  
|[uppercase](#fmtflags)|指定在進行某些插入時，插入小寫字母的大寫對應。|  
  
### <a name="member-functions"></a>成員函式  
  
|||  
|-|-|  
|[failure](#failure)|成員類別會作為範本類別 [basic_ios](../standard-library/basic-ios-class.md) 中成員函式 [clear](../standard-library/basic-ios-class.md#clear) 所擲回之所有例外狀況的基底類別。|  
|[flags](#flags)|設定或傳回目前的旗標設定。|  
|[getloc](#getloc)|傳回儲存的地區設定物件。|  
|[imbue](#imbue)|變更地區設定。|  
|[Init](#init)|建構時建立標準 iostream 物件。|  
|[iword](#iword)|指派將值儲存為 `iword`。|  
|[precision](#precision)|指定要在浮點數顯示的數字位數。|  
|[pword](#pword)|指派將值儲存為 `pword`。|  
|[register_callback](#register_callback)|指定回呼函式。|  
|[setf](#setf)|設定指定的旗標。|  
|[sync_with_stdio](#sync_with_stdio)|可確保 iostream 和 C 執行階段程式庫作業依照它們在原始程式碼中出現的順序發生。|  
|[unsetf](#unsetf)|使指定的旗標為關閉。|  
|[width](#width)|設定輸出資料流的長度。|  
|[xalloc](#xalloc)|指定變數應該是資料流的一部分。|  
  
### <a name="operators"></a>運算子  
  
|||  
|-|-|  
|[operator=](#op_eq)|`ios_base` 物件的指派運算子。|  
  
## <a name="requirements"></a>需求  
 **標頭：**\<ios>  
  
 **命名空間：** std  
  
##  <a name="event"></a>  ios_base::event  
 指定事件類型。  
  
```  
enum event {
    erase_event,
    imbue_event,
    copyfmt_event};  
```  
  
### <a name="remarks"></a>備註  
 此類型為列舉類型，描述可以儲存回呼事件的物件，此事件是用來作為以 [register_callback](#register_callback) 註冊之函式的引數。 不同的事件值如下：  
  
- **copyfmt_event**：識別在接近對 [copyfmt](../standard-library/basic-ios-class.md#copyfmt) 的呼叫結尾、緊接在複製[例外狀況遮罩](../standard-library/ios-base-class.md)之前發生的回呼。  
  
- **erase_event**：識別在對 [copyfmt](../standard-library/basic-ios-class.md#copyfmt) 的呼叫開頭或在對 **\*this** 之解構函式的呼叫開頭發生的回呼。  
  
- **imbue_event**：識別在對 [imbue](#imbue) 的呼叫結尾、緊接在函式返回之前發生的回呼。  
  
### <a name="example"></a>範例  
  
  如需範例，請參閱 [register_callback](#register_callback)。  
  
##  <a name="event_callback"></a>  ios_base::event_callback  

 描述傳遞給 [register_call](#register_callback) 的函式。  
  
```  
typedef void (__cdecl *event_callback)(
    event _E,  
    ios_base& _Base,  
    int _I);
```  
  
### <a name="parameters"></a>參數  
 *_E*  
 [事件](#event)。  
  
 `_Base`  
 在其中呼叫事件的資料流。  
  
 *_I*  
 使用者定義的數字。  
  
### <a name="remarks"></a>備註  
  
 此類型描述一個可藉由 [register_callback](#register_callback) 註冊之函式的指標。 此類型的函式不得擲回例外狀況。  
  
### <a name="example"></a>範例  
  
  如需使用 `event_callback` 的範例，請參閱 [register_call](#register_callback)。  
  
##  <a name="failure"></a>  ios_base::failure  
  
 類別 `failure` 可為以例外狀況方式擲回之所有物件的類型定義基底類別，這些例外狀況是 `iostreams` 程式庫中的函式所擲回，用來回報在資料流緩衝作業期間偵測到的錯誤。  
  
```  
namespace std {  
    class failure : public system_error {  
    public:  
        explicit failure(
            const string& _Message,  
            const error_code& _Code = io_errc::stream);

        explicit failure(
            const char* str,  
            const error_code& _Code = io_errc::stream);
    };
}  
```  
  
### <a name="remarks"></a>備註  

 `what()` 所傳回的值是 `_Message` 的複本，此複本可能根據 `_Code` 隨測試擴增。 如果未指定 `_Code`，則預設值為 `make_error_code(io_errc::stream)`。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_base_failure.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.exceptions(ios::failbit);  
    try  
    {  
        file.open( "rm.txt", ios_base::in );  
        // Opens nonexistent file for reading  
    }  
    catch( ios_base::failure f )  
    {  
        cout << "Caught an exception: " << f.what() << endl;  
    }  
}  
```  
  
```Output  
Caught an exception: ios_base::failbit set  
```  
  
##  <a name="flags"></a>  ios_base::flags  
  
 設定或傳回目前的旗標設定。  
  
```  
fmtflags flags() const;
fmtflags flags(fmtflags fmtfl);
```  
  
### <a name="parameters"></a>參數  
 `fmtfl`  
 新的 `fmtflags` 設定。  
  
### <a name="return-value"></a>傳回值  
  
 先前或目前的 `fmtflags` 設定。  
  
### <a name="remarks"></a>備註  
  
 如需旗標的清單，請參閱 [ios_base::fmtflags](#fmtflags)。  
  
 第一個成員函式會傳回已儲存的格式旗標。 第二個成員函式會在格式旗標中儲存 `fmtfl`，並傳回其先前儲存的值。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_base_flags.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    cout << cout.flags( ) << endl;  
    cout.flags( ios::dec | ios::boolalpha );  
    cout << cout.flags( );  
}    
```  
  
```Output  
513  
16896  
```  
  
##  <a name="fmtflags"></a>  ios_base::fmtflags  
  
 指定輸出外觀的常數。  
  
```
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type fmtflags;  
   static const fmtflags boolalpha;  
   static const fmtflags dec;  
   static const fmtflags fixed;  
   static const fmtflags hex;  
   static const fmtflags internal;  
   static const fmtflags left;  
   static const fmtflags oct;  
   static const fmtflags right;  
   static const fmtflags scientific;  
   static const fmtflags showbase;  
   static const fmtflags showpoint;  
   static const fmtflags showpos;  
   static const fmtflags skipws;  
   static const fmtflags unitbuf;  
   static const fmtflags uppercase;  
   static const fmtflags adjustfield;  
   static const fmtflags basefield;  
   static const fmtflags floatfield;  
   // ...  
};  
```  
  
### <a name="remarks"></a>備註  
  
 支援 [ios](../standard-library/ios.md) 中的操作工具。  
  
 此類型為位元遮罩類型，描述可以儲存格式旗標的物件。 不同的旗標值 (項目) 為：  
  
- `dec`，以十進位格式插入或擷取整數值。  
  
- `hex`，以十六進位格式插入或擷取整數值。  
  
- `oct`，以八進位格式插入或擷取整數值。  
  
- `showbase`，插入可顯示所產生整數欄位之基底的前置詞。  
  
- `internal`，藉由在產生的數字欄位內部一點中插入填滿字元，來視需要填補欄位寬度。 (如需有關設定欄位寬度的詳細資訊，請參閱 [setw](../standard-library/iomanip-functions.md#setw))。  
  
- `left`，藉由插入填滿字元到所產生欄位的結尾，來視需要填補欄位寬度 (靠左對齊)。  
  
- `right`，藉由插入填滿字元到所產生欄位的開頭，來視需要填補欄位寬度 (靠右對齊)。  
  
- `boolalpha`，以名稱形式 (例如 `true` 和 `false`) 而非數值，來插入或擷取類型 `bool` 的物件。  
  
- `fixed`，以固定點格式插入浮點數值 (沒有指數欄位)。  
  
- `scientific`，以科學記號格式插入浮點數值 (具有一個指數欄位)。  
  
- `showpoint`，在產生的浮點欄位無條件插入小數點。  
  
- `showpos`，在產生的非負數字欄位插入加號。  
  
- `skipws`，在進行某些擷取前，略過前置空白字元。  
  
- `unitbuf`，在進行每次插入之後清除輸出。  
  
- `uppercase`，在進行某些插入時，插入小寫字母的大寫對應。  
  
 此外，許多有用的值如下：  
  
- `adjustfield`：一個以 `internal` &#124; `left` &#124; `right` 方式定義的位元遮罩  
  
- `basefield`：以 `dec` &#124; `hex` &#124; `oct` 方式定義  
  
- `floatfield`：以 `fixed` &#124; `scientific` 方式定義  
  
 如需修改這些格式旗標的函式範例，請參閱 [\<iomanip>](../standard-library/iomanip.md)。  
  
##  <a name="getloc"></a>  ios_base::getloc  
  
 傳回儲存的地區設定物件。  
  
```  
locale getloc() const;
```  
  
### <a name="return-value"></a>傳回值  
  
 已儲存的地區設定物件。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_base_getlock.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    cout << cout.getloc( ).name( ).c_str( ) << endl;  
}  
```  
  
```Output  
C  
```  
  
##  <a name="imbue"></a>  ios_base::imbue  

 變更地區設定。  
  
```  
locale imbue(const locale& _Loc);
```  
  
### <a name="parameters"></a>參數  
 `_Loc`  
 新的地區設定。  
  
### <a name="return-value"></a>傳回值  
  
 先前的地區設定。  
  
### <a name="remarks"></a>備註  
  
 成員函式會在地區設定物件中儲存 `_Loc`，然後回報回呼事件和 `imbue_event`。 它會傳回先前儲存的值。  
  
### <a name="example"></a>範例  
  
  如需範例，請參閱 [basic_ios::imbue](../standard-library/basic-ios-class.md#imbue)。  
  
##  <a name="init"></a>  ios_base::Init  
  
 建構時建立標準 iostream 物件。  
  
```  
class Init { };  
```
  
### <a name="remarks"></a>備註  
  
 此巢狀類別會描述一個物件，其中此物件的建構可確保以正確方式建構標準 iostream 物件，甚至是在執行任意靜態物件的建構函式之前。  
  
##  <a name="ios_base"></a>  ios_base::ios_base  
  
 建構 ios_base 物件。  
  
```  
ios_base();
```  
  
### <a name="remarks"></a>備註  
  
 (受保護的) 建構函式不會執行任何動作。 稍後對 **basic_ios::**[init](../standard-library/basic-ios-class.md#init) 的呼叫必須先將物件初始化，之後才能將它安全地終結。 因此，ios_base 類別的唯一安全用法就是當作範本類別 [basic_ios](../standard-library/basic-ios-class.md) 的基底類別。  
  
##  <a name="iostate"></a>  ios_base::iostate  
  
 描述資料流狀態的常數類型。  
  
```  
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type iostate;  
   static const iostate badbit;  
   static const iostate eofbit;  
   static const iostate failbit;  
   static const iostate goodbit;  
   // ...  
};  
```  
  
### <a name="remarks"></a>備註  
  
 此類型為位元遮罩類型，描述可以儲存資料流狀態資訊的物件。 不同的旗標值 (項目) 為：  
  
- `badbit`：記錄資料流緩衝區的完整性減損。  
  
- `eofbit`：從資料流擷取時記錄檔案結尾。  
  
- `failbit`：記錄從資料流擷取有效欄位時的失敗。  
  
 此外，還有一個有用的值 `goodbit`，其中未設定先前提到的任何位元 (`goodbit` 保證為零)。  
  
##  <a name="iword"></a>  ios_base::iword  
  
 指派將值儲存為 `iword`。  
  
```  
long& iword(int idx);
```  
  
### <a name="parameters"></a>參數  
 `idx`  
 要以 `iword` 形式儲存之值的索引。  
  
### <a name="remarks"></a>備註  
  
 成員函式會傳回對可延伸陣列之元素 `idx` 的參考，該陣列含有 **long** 類型的元素。 所有元素都實際存在，且一開始儲存的值為零。 在下一次呼叫物件的 `iword` 之後、在呼叫 **basic_ios::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt) 來更改物件之後，或在終結物件之後，傳回的參考便無效。  
  
 如果 `idx` 是負數或是沒有唯一儲存體可供元素使用，函式就會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)**，並傳回可能並非唯一的參考。  
  
 若要取得唯一索引以在 `ios_base` 類型的所有物件上使用，請呼叫 [xalloc](#xalloc)。  
  
### <a name="example"></a>範例  
  
  如需如何使用 `iword` 的範例，請參閱 [xalloc](#xalloc)。  
  
##  <a name="openmode"></a>  ios_base::openmode  
  
 描述如何與資料流互動。  
  
```  
class ios_base {  
public:  
   typedef implementation-defined-bitmask-type iostate;  
   static const iostate badbit;  
   static const iostate eofbit;  
   static const iostate failbit;  
   static const iostate goodbit;  
   // ...  
};  
```  
  
### <a name="remarks"></a>備註  
  
 此類型為 `bitmask type`，描述可以儲存數個 iostreams 物件之開啟模式的物件。 不同的旗標值 (項目) 為：  
  
- **app**：在每次插入之前搜尋到資料流的結尾。  
  
- **ate**：在第一次建立資料流的控制物件時搜尋到資料流的結尾。  
  
- **binary**：將檔案當作二進位資料流來讀取，而不是當作文字資料流。  
  
- **in**：允許從資料流擷取。  
  
- **out**：允許插入到資料流中。  
  
- **trunc**：在建立現有檔案的控制物件時刪除該檔案的內容。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_base_openmode.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.open( "rm.txt", ios_base::out | ios_base::trunc );  
    
    file << "testing";  
}    
```  
  
##  <a name="op_eq"></a>  ios_base::operator=  

 ios_base 物件的指派運算子。  
  
```  
ios_base& operator=(const ios_base& right);
```  
  
### <a name="parameters"></a>參數  
 `right`  
 `ios_base` 類型的物件。  
  
### <a name="return-value"></a>傳回值  
  
 要作為指派對象的物件。  
  
### <a name="remarks"></a>備註  
  
 運算子會複製已儲存的格式設定資訊，建立任何可延伸陣列的新複本。 然後傳回 **\*this**。 請注意，並不會複製回呼堆疊。  
  
 此運算子僅供衍生自 `ios_base` 的類別使用。  
  
##  <a name="precision"></a>  ios_base::precision  
  
 指定要在浮點數顯示的數字位數。  
  
```  
streamsize precision() const;
streamsize precision(streamsize _Prec);
```  
  
### <a name="parameters"></a>參數  
 `_Prec`  
 要顯示的有效位數，或是固定標記法中的小數點後位數。  
  
### <a name="return-value"></a>傳回值  
  
 第一個成員函式會傳回已儲存的[顯示整數位數](../standard-library/ios-base-class.md)。 第二個成員函式會在顯示整數位數中儲存 `_Prec`，並傳回其先前儲存的值。  
  
### <a name="remarks"></a>備註  
  
 浮點數會使用 [fixed](../standard-library/ios-functions.md#fixed) 以固定標記法顯示。  
  
### <a name="example"></a>範例  
  
```cpp  
// ios_base_precision.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    float i = 31.31234F;  
    
    cout.precision( 3 );  
    cout << i << endl;          // display three significant digits  
    cout << fixed << i << endl; // display three digits after decimal  
                                // point  
}  
```  
  
```Output  
31.3  
31.312  
```  
  
##  <a name="pword"></a>  ios_base::pword  
  
 指派將值儲存為 `pword`。  
  
```  
void *& pword(int _Idx);
```  
  
### <a name="parameters"></a>參數  
 `_Idx`  
 要以 `pword` 形式儲存之值的索引。  
  
### <a name="remarks"></a>備註  
  
 成員函式會傳回對可延伸陣列之元素 _ *Idx* 的參考，該陣列含有類型 `void` 旗標的元素。 所有元素都實際存在，且一開始儲存 Null 指標。 在下一次呼叫物件的 `pword` 之後、在呼叫 **basic_ios::**[copyfmt](../standard-library/basic-ios-class.md#copyfmt) 來更改物件之後，或在終結物件之後，傳回的參考便無效。  
  
 如果 _ *Idx* 是負數或是沒有唯一儲存體可供元素使用，函式就會呼叫 [setstate](../standard-library/basic-ios-class.md#setstate)**(badbit)**，並傳回可能並非唯一的參考。  
  
 若要取得唯一索引以在 `ios_base` 類型的所有物件上使用，請呼叫 [xalloc](#xalloc)。  
  
### <a name="example"></a>範例  
  
  如需使用 `pword` 的範例，請參閱 [xalloc](#xalloc)。  
  
##  <a name="register_callback"></a>  ios_base::register_callback  
  
 指定回呼函式。  
  
```  
void register_callback(
    event_callback pfn, int idx);
```  
  
### <a name="parameters"></a>參數  
 `pfn`  
 回呼函式的指標。  
  
 `idx`  
 使用者定義的數字。  
  
### <a name="remarks"></a>備註  
  
 成員函式推播通知組`{pfn, idx}`至預存的回呼堆疊[回呼堆疊](../standard-library/ios-base-class.md)。 當回呼事件**ev**報告，函式的呼叫，以相反順序的登錄中，運算式`(*pfn)(ev, *this, idx)`。  
 
### <a name="example"></a>範例  
  
```cpp  
// ios_base_register_callback.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
using namespace std;  
  
void callback1( ios_base::event e, ios_base& stream, int arg )  
{  
    cout << "in callback1" << endl;  
    switch ( e )  
    {  
    case ios_base::erase_event:  
        cout << "an erase event" << endl;  
        break;  
    case ios_base::imbue_event:  
        cout << "an imbue event" << endl;  
        break;  
    case ios_base::copyfmt_event:  
        cout << "an copyfmt event" << endl;  
        break;  
    };  
}  
  
void callback2( ios_base::event e, ios_base& stream, int arg )  
{  
    cout << "in callback2" << endl;  
    switch ( e )  
    {  
    case ios_base::erase_event:  
        cout << "an erase event" << endl;  
        break;  
    case ios_base::imbue_event:  
        cout << "an imbue event" << endl;  
        break;  
    case ios_base::copyfmt_event:  
        cout << "an copyfmt event" << endl;  
        break;  
    };  
}  
  
int main( )  
{  
    // Make sure the imbue will not throw an exception  
    // assert( setlocale( LC_ALL, "german" )!=NULL );  
    
    cout.register_callback( callback1, 0 );  
    cin.register_callback( callback2, 0 );  
    
    try  
    {  
        // If no exception because the locale's not found,  
        // generate an imbue_event on callback1  
        cout.imbue(locale("german"));  
    }  
    catch(...)  
    {  
        cout << "exception" << endl;  
    }  
    
    // This will  
    // (1) erase_event on callback1  
    // (2) copyfmt_event on callback2  
    cout.copyfmt(cin);  
    
    // We get two erase events from callback2 at the end because  
    // both cin and cout have callback2 registered when cin and cout  
    // are destroyed at the end of program.  
}  
```  
  
```Output  
in callback1  
an imbue event  
in callback1  
an erase event  
in callback2  
an copyfmt event  
in callback2  
an erase event  
in callback2  
an erase event  
```  
 
##  <a name="seekdir"></a> ios_base::seekdir  
  
指定位移作業的起點。  
  
```  
namespace std {  
    class ios_base {  
    public:  
        typedef implementation-defined-enumerated-type seekdir;  
        static const seekdir beg;  
        static const seekdir cur;  
        static const seekdir end;  
        // ...  
    };  
}  
```  
 
### <a name="remarks"></a>備註  
  
此類型為列舉的類型，描述可以儲存數個 iostream 類別的成員函式的引數所做的搜尋模式的物件。 不同的旗標值為：  
 
- **beg**：進行相對於序列 (陣列、資料流或檔案) 開頭的搜尋 (更改目前的讀取或寫入位置)。  
 
- **cur**：進行相對於序列內目前位置的搜尋。  
 
- **end**：進行相對於序列結尾的搜尋。  
 
### <a name="example"></a>範例  
  
```cpp  
// ios_base_seekdir.cpp  
// compile with: /EHsc  
#include <iostream>  
#include <fstream>  
  
int main ( )  
{  
    using namespace std;  
    fstream file;  
    file.open( "rm.txt", ios_base::out | ios_base::trunc );  
    
    file << "testing";  
    file.seekp( 0, ios_base::beg );  
    file << "a";  
    file.seekp( 0, ios_base::end );  
    file << "a";  
}  
```  
  
##  <a name="setf"></a> ios_base::setf  
  
設定指定的旗標。  

```    
fmtflags setf(  
    fmtflags _Mask  
);  
fmtflags setf(  
    fmtflags _Mask,  
    fmtflags _Unset  
);  
```  
 
### <a name="parameters"></a>參數  
 `_Mask`  
    要開啟的旗標。  
 
 *_Unset*關閉旗標。  
 
### <a name="return-value"></a>傳回值  
    The previous format flags  
 
### <a name="remarks"></a>備註  
    The first member function effectively calls [flags](#flags)(_ *Mask* &#124; \_ *Flags*) (set selected bits) and then returns the previous format flags. The second member function effectively calls **flags**(\_ *Mask* **& fmtfl, flags& ~**`_Mask`) (replace selected bits under a mask) and then returns the previous format flags.  
 
### <a name="example"></a>範例  
  
```cpp  
// ios_base_setf.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    int i = 10;  
    cout << i << endl;  
    
    cout.unsetf( ios_base::dec );  
    cout.setf( ios_base::hex );  
    cout << i << endl;  
    
    cout.setf( ios_base::dec );  
    cout << i << endl;  
    cout.setf( ios_base::hex, ios_base::dec );  
    cout << i << endl;  
}  
```  
 
##  <a name="sync_with_stdio"></a> ios_base::sync_with_stdio  
  
可確保 iostream 和 C 執行階段程式庫作業依照它們在原始程式碼中出現的順序發生。  
  
```  
static bool sync_with_stdio(  
   bool _Sync = true  
);  
```  
 
### <a name="parameters"></a>參數  
 `_Sync`  
    所有資料流是否與 **stdio** 同步。  
 
### <a name="return-value"></a>傳回值  
    Previous setting for this function.  
 
### <a name="remarks"></a>備註  
    The static member function stores a **stdio** sync flag, which is initially **true**. When **true**, this flag ensures that operations on the same file are properly synchronized between the [iostreams](../standard-library/iostreams-conventions.md) functions and those defined in the C++ Standard Library. Otherwise, synchronization may or may not be guaranteed, but performance may be improved. The function stores `_Sync` in the **stdio** sync flag and returns its previous stored value. You can call it reliably only before performing any operations on the standard streams.  
 
##  <a name="unsetf"></a> ios_base::unsetf  
  
使指定的旗標為關閉。  
  
```  
void unsetf(  
   fmtflags _Mask  
);  
```  
 
### <a name="parameters"></a>參數  
 `_Mask`  
    您想要關閉的旗標。  
 
### <a name="remarks"></a>備註  
    The member function effectively calls [flags](#flags)(`~`*_Mask* **& flags**) (clear selected bits).  
 
### <a name="example"></a>範例  
    See [ios_base::setf](#setf) for a sample of using `unsetf`.  
 
##  <a name="width"></a> ios_base::width  
  
設定輸出資料流的長度。  
  
```  
streamsize width( ) const;  
streamsize width(  
   streamsize _Wide  
);  
```  
 
### <a name="parameters"></a>參數  
 `_Wide`  
    所需的輸出資料流大小。  
 
### <a name="return-value"></a>傳回值  

    The current width setting.  
 
### <a name="remarks"></a>備註  

    The first member function returns the stored field width. The second member function stores `_Wide` in the field width and returns its previous stored value.  
 
### <a name="example"></a>範例  
  
```cpp  
// ios_base_width.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main( ) {  
    using namespace std;  
    
    cout.width( 20 );  
    cout << cout.width( ) << endl;  
    cout << cout.width( ) << endl;  
}  
```  
  
```Output  
20  
0  
```  
 
##  <a name="xalloc"></a> ios_base::xalloc  
  
    Specifies that a variable is part of the stream.  
  
```  
static int xalloc( );  
```  
 
### <a name="return-value"></a>傳回值  
    The static member function returns a stored static value, which it increments on each call.  
 
### <a name="remarks"></a>備註  
    You can use the return value as a unique index argument when calling the member functions [iword](#iword) or [pword](#pword).  
 
### <a name="example"></a>範例  
  
```cpp  
// ios_base_xalloc.cpp  
// compile with: /EHsc  
// Lets you store user-defined information.  
// iword, jword, xalloc  
#include <iostream>  
  
int main( )  
{  
    using namespace std;  
    
    static const int i = ios_base::xalloc();  
    static const int j = ios_base::xalloc();  
    cout.iword( i ) = 11;  
    cin.iword( i ) = 13;  
    cin.pword( j ) = "testing";  
    cout << cout.iword( i ) << endl;  
    cout << cin.iword( i ) << endl;  
    cout << ( char * )cin.pword( j ) << endl;  
}    
```  
  
```Output  
11  
13  
testing  
```  
  
## <a name="see-also"></a>另請參閱  
 [C++ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostream 慣例](../standard-library/iostreams-conventions.md)
