---
title: "&lt;sstream&gt; | Microsoft Docs"
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
  - "std.<sstream>"
  - "std::<sstream>"
  - "<sstream>"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "sstream 標頭"
ms.assetid: 56f55bc5-549d-4e7f-aaad-99e0ffa49c9e
caps.latest.revision: 20
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# &lt;sstream&gt;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

定義支援在配置陣列物件儲存的 iostreams 作業的範本類別。  這類序列加入至樣板類別可自動轉換為 [basic\_string](../standard-library/basic-string-class.md)物件。  
  
## 語法  
  
```  
namespace std {  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringbuf;  
typedef basic_stringbuf<char> stringbuf;  
typedef basic_stringbuf<wchar_t> wstringbuf;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_istringstream;  
typedef basic_istringstream<char> istringstream;  
typedef basic_istringstream<wchar_t> wistringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_ostringstream;  
typedef basic_ostringstream<char> ostringstream;  
typedef basic_ostringstream<wchar_t> wostringstream;  
  
template<class CharType,  
    class Traits = char_traits<CharType>,  
    class Allocator = allocator<CharType> >  
    class basic_stringstream;  
typedef basic_stringstream<char> stringstream;  
typedef basic_stringstream<wchar_t> wstringstream;  
  
        // TEMPLATE FUNCTIONS  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_stringbuf<CharType, Traits, Allocator>& _Left,  
        basic_stringbuf<CharType, Traits, Allocator>& _Right  
    );   
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_istringstream<CharType, Traits, Allocator>& _Left,  
        basic_istringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap(  
        basic_ostringstream<CharType, Traits, Allocator>& _Left,  
        basic_ostringstream<CharType, Traits, Allocator>& _Right  
    );  
template<class CharType, class Traits, class Allocator>  
    void swap (  
        basic_stringstream<CharType, Traits, Allocator>& _Left,  
        basic_stringstream<CharType, Traits, Allocator>& _Right  
    );  
}  // namespace std  
  
```  
  
#### 參數  
  
|參數|說明|  
|--------|--------|  
|`_Left`|對 `sstream` 物件的參考。|  
|`_Right`|對 `sstream` 物件的參考。|  
  
## 備註  
 型別 `char *` 物件在 [\<strstream\>](../standard-library/strstream.md) 可以使用功能為資料流。  不過， `<strstream>` 已被取代，並使用 `<sstream>` 盡量。  
  
### Typedef  
  
|||  
|-|-|  
|[istringstream](../Topic/istringstream.md)|建立型別在 `char` 樣板參數特製化的 `basic_istringstream` 。|  
|[ostringstream](../Topic/ostringstream.md)|建立型別在 `char` 樣板參數特製化的 `basic_ostringstream` 。|  
|[stringbuf](../Topic/stringbuf.md)|建立型別在 `char` 樣板參數特製化的 `basic_stringbuf` 。|  
|[stringstream](../Topic/stringstream.md)|建立型別在 `char` 樣板參數特製化的 `basic_stringstream` 。|  
|[wistringstream](../Topic/wistringstream.md)|建立型別在 `wchar_t` 樣板參數特製化的 `basic_istringstream` 。|  
|[wostringstream](../Topic/wostringstream.md)|建立型別在 `wchar_t` 樣板參數特製化的 `basic_ostringstream` 。|  
|[wstringbuf](../Topic/wstringbuf.md)|建立型別在 `wchar_t` 樣板參數特製化的 `basic_stringbuf` 。|  
|[wstringstream](../Topic/wstringstream.md)|建立型別在 `wchar_t` 樣板參數特製化的 `basic_stringstream` 。|  
  
### 操作工具  
  
|||  
|-|-|  
|[交換](../Topic/%3Csstream%3E%20swap.md)|若要在兩個 `sstream` 物件之間的值。|  
  
### 類別  
  
|||  
|-|-|  
|[basic\_stringbuf](../standard-library/basic-stringbuf-class.md)|往返於陣列物件中的元素順序描述控制項型別 **Elem**的項目傳輸，性格特性類別取決於 **Tr**資料流緩衝區。|  
|[basic\_istringstream](../standard-library/basic-istringstream-class.md)|描述物件項目的控制項擷取並輸入從類別 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**， **Tr**， `Alloc`\>資料流緩衝區的物件，其中含有型別 **Elem**的元素，類別取決於性格特性 **Tr**，因此，項目會依類別配置 `Alloc`配置器。|  
|[basic\_ostringstream](../standard-library/basic-ostringstream-class.md)|描述物件項目的控制項插入並輸入物件的類別 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<**Elem**， **Tr**， `Alloc`\>資料流緩衝區，以型別 **Elem**的元素，類別取決於性格特性 **Tr**，因此，項目會依類別配置 `Alloc`配置器。|  
|[basic\_stringstream](../standard-library/basic-stringstream-class.md)|描述物件控制項目的插入和擷取並輸入物件使用 [basic\_stringbuf](../standard-library/basic-stringbuf-class.md)\<類別，**ElemTr**， `Alloc`\>資料流緩衝區，以型別 **Elem**的元素，類別取決於性格特性 **Tr**，因此，項目會依類別配置 `Alloc`配置器。|  
  
## 需求  
  
-   **標題:** \<sstream\>  
  
-   **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)