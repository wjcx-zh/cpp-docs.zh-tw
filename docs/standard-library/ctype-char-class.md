---
title: "ctype &lt; char &gt; 類別 | Microsoft Docs"
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
  - "ctype<char>"
  - "locale/std::ctype<char>"
  - "std::ctype<char>"
  - "std.ctype<char>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "ctype < char > 類別"
ms.assetid: ee30acb4-a743-405e-b3d4-13602092da84
caps.latest.revision: 20
caps.handback.revision: 20
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# ctype &lt; char &gt; 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

類別是類別樣板的明確特製化 **ctype \< CharType**> 輸入 `char`, ，描述可以做為地區設定 facet 各種屬性的類型的字元特性的物件 `char`。  
  
## <a name="syntax"></a>語法  
  
```  
template <>  
class ctype<char>  
: public ctype_base  
{  
public:  
    typedef char _Elem;  
    typedef _Elem char_type;  
    bool is(
    mask _Maskval,  
    _Elem _Ch) const;

 
    const _Elem* is(
    const _Elem* first,  
    const _Elem* last,  
    mask* dest) const;

 
    const _Elem* scan_is(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    const _Elem* scan_not(
    mask _Maskval,  
    const _Elem* first,  
    const _Elem* last) const;

 
    _Elem tolower(
    _Elem _Ch) const;

 
    const _Elem* tolower(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem toupper(
    _Elem _Ch) const;

 
    const _Elem* toupper(
    _Elem* first,  
    const _Elem* last) const;

 
    _Elem widen(
    char _Byte) const;

 
    const _Elem* widen(
    const char* first,  
    const char* last,  
    _Elem* dest) const;

 
    const _Elem* _Widen_s(
    const char* first,  
    const char* last,  
    _Elem* dest,  
    size_t dest_size) const;

 
    _Elem narrow(
    _Elem _Ch,  
    char _Dflt = '\0') const;

 
    const _Elem* narrow(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest) const;

 
    const _Elem* _Narrow_s(
    const _Elem* first,  
    const _Elem* last,  
    char _Dflt,  
    char* dest,  
    size_t dest_size) const;

 
    static locale::id& id;  
    explicit ctype(
    const mask* _Table = 0,  
    bool _Deletetable = false,  
    size_t _Refs = 0);

protected:  
    virtual ~ctype();
//other protected members  
};  
```  
  
## <a name="remarks"></a>備註  
 明確特製化不同於樣板類別，以數種方式︰  
  
-   Ctype 類別的物件 < `char`> 儲存指標至 ctype 遮罩表格的第一個項目、 UCHAR_MAX 陣列 + 1 個項目的型別 **ctype_base::mask**。 它也會儲存布林值的物件，指出是否應該刪除陣列 (使用 `operator delete[]`) 時 ctype \< **Elem**> 物件被終結。  
  
-   其唯一的公用建構函式可讓您指定 **] 索引標籤**, ，ctype 遮罩資料表和 **del**, ，如果應該是陣列則為 true 的布林物件刪除 ctype < `char`> 物件被終結，以及參考計數參數參考。  
  
-   受保護的成員函式 **資料表** 傳回預存的 ctype 遮罩資料表。  
  
-   靜態成員物件 **table_size** ctype 遮罩資料表中指定的項目數目下限。  
  
-   受保護的靜態成員函式 **classic_table**（傳回 ctype 遮罩表格配合"C"地區設定。  
  
-   沒有受保護的虛擬成員函式 [do_is](../standard-library/ctype-class.md#ctype__do_is), ，[do_scan_is](../standard-library/ctype-class.md#ctype__do_scan_is), ，或 [do_scan_not](../standard-library/ctype-class.md#ctype__do_scan_not)。 對應的公用成員函式執行本身的對等作業。  
  
 成員函式 [do_narrow](../standard-library/ctype-class.md#ctype__do_narrow) 和 [do_widen](../standard-library/ctype-class.md#ctype__do_widen) 複製項目不變。  
  
## <a name="requirements"></a>需求  
 **標頭︰** \< 地區設定>  
  
 **命名空間︰** std  
  
## <a name="see-also"></a>請參閱  
 [facet 類別](../Topic/facet%20Class.md)   
 [ctype_base 類別](../standard-library/ctype-base-class.md)   
 [C + + 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)

