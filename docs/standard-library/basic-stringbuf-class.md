---
title: "basic_stringbuf 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "basic_stringbuf"
  - "sstream/std::basic_stringbuf"
  - "std.basic_stringbuf"
  - "std::basic_stringbuf"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_stringbuf 類別"
ms.assetid: 40c85f9e-42a5-4a65-af5c-23c8e3bf8113
caps.latest.revision: 28
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 28
---
# basic_stringbuf 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述資料流緩衝區，其控制類型 `Elem` 的項目 \(其字元特性由類別 `Tr` 所決定\)，與陣列物件中儲存的項目序列之間的往來傳輸。  
  
## 語法  
  
```  
template <class Elem, class Tr = char_traits<Elem>,   
   class Alloc = allocator<Elem>   
>  
   class basic_stringbuf : public basic_streambuf<Elem, Tr>  
```  
  
#### 參數  
 `Alloc`  
 配置器類別。  
  
 `Elem`  
 字串之基本項目的類型。  
  
 `Tr`  
 字元特性是在字串的基本項目上特製化。  
  
## 備註  
 會視需要配置、擴充和釋出物件，以容納序列中的變更。  
  
 類別 basic\_stringbuf\<`Elem`, `Tr`, `Alloc`\> 的物件會從其建構函式儲存 `ios_base::`[openmode](../Topic/ios_base::openmode.md) 引數的複本，以做為其 `stringbuf` 模式 **模式**：  
  
-   如果 `mode & ios_base::in` 非零，輸入緩衝區即可存取。 如需詳細資訊，請參閱[basic\_streambuf 類別](../standard-library/basic-streambuf-class.md)。  
  
-   如果 `mode & ios_base::out` 非零，輸出緩衝區即可存取。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_stringbuf](../Topic/basic_stringbuf::basic_stringbuf.md)|建構類型 `basic_stringbuf` 的物件。|  
  
### Typedefs  
  
|||  
|-|-|  
|[allocator\_type](../Topic/basic_stringbuf::allocator_type.md)|此類型是樣板參數 `Alloc` 的同義字。|  
|[char\_type](../Topic/basic_stringbuf::char_type.md)|將類型名稱與 `Elem` 樣板參數產生關聯。|  
|[int\_type](../Topic/basic_stringbuf::int_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[off\_type](../Topic/basic_stringbuf::off_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[pos\_type](../Topic/basic_stringbuf::pos_type.md)|在 `basic_filebuf` 的範圍中製作此類型，相當於在 `Tr` 範圍中的同名類型。|  
|[traits\_type](../Topic/basic_stringbuf::traits_type.md)|將類型名稱與 `Tr` 樣板參數產生關聯。|  
  
### 成員函式  
  
|||  
|-|-|  
|[Overflow \- 溢位](../Topic/basic_stringbuf::overflow.md)|受保護的虛擬函式，可在將新字元插入已滿的緩衝區時呼叫。|  
|[pbackfail](../Topic/basic_stringbuf::pbackfail.md)|受保護的虛擬成員函式會嘗試將項目放回輸入緩衝區，然後將其設成目前的項目 \(由下一個指標指向\)。|  
|[seekoff](../Topic/basic_stringbuf::seekoff.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[seekpos](../Topic/basic_stringbuf::seekpos.md)|受保護的虛擬成員函式會嘗試改變受控制資料流的目前位置。|  
|[str](../Topic/basic_stringbuf::str.md)|設定或取得字串緩衝區中的文字，而不需要變更寫入位置。|  
|swap||  
|[溢位](../Topic/basic_stringbuf::underflow.md)|用於從輸入資料流擷取目前項目之受保護的虛擬成員函式。|  
  
## 需求  
 **標頭：**\<sstream\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)