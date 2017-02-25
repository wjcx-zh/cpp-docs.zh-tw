---
title: "basic_ios 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.basic_ios"
  - "ios/std::basic_ios"
  - "basic_ios"
  - "std::basic_ios"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "basic_ios 類別"
ms.assetid: 4fdcd8e1-62d2-4611-8a70-1e4f58434007
caps.latest.revision: 24
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 24
---
# basic_ios 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此範本類別說明依存於範本參數的輸入資料流 \(屬於範本類別 [basic\_istream](../standard-library/basic-istream-class.md)\) 和輸出資料流 \(屬於範本類別 [basic\_ostream](../standard-library/basic-ostream-class.md)\) 通用的儲存體和成員函式。  \(此類別 [ios\_base](../standard-library/ios-base-class.md) 描述範本參數上何者常用且不相依。\) **basic\_ios\<class Elem, class Traits\>** 類別的物件協助以 **Elem** 類型項目控制資料流，其字元特性由類別 **Traits** 所決定。  
  
## 語法  
  
```  
  
     template <class   
     Elem  
     , class   
     Traits  
     >  
class basic_ios : public ios_base  
```  
  
#### 參數  
 `Elem`  
 類型。  
  
 `Traits`  
 類型為 `char_traits` 的變數。  
  
## 備註  
 **basic\_ios\<class Elem, class Traits\>** 類別的物件會儲存：  
  
-   [basic\_istream](../standard-library/basic-istream-class.md) **\<Elem, Traits\>** 類型物件的繫結指標。  
  
-   [basic\_streambuf](../standard-library/basic-streambuf-class.md) **\<Elem, Traits \>** 類型物件的資料流緩衝區指標。  
  
-   [格式化資訊](../standard-library/ios-base-class.md)。  
  
-   [ios\_base](../standard-library/ios-base-class.md) 類型基底物件中的[資料流狀態資訊](../standard-library/ios-base-class.md)。  
  
-   `char_type` 類型物件中的填滿字元。  
  
### 建構函式  
  
|||  
|-|-|  
|[basic\_ios](../Topic/basic_ios::basic_ios.md)|建構 `basic_ios` 類別。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/basic_ios::char_type.md)|`Elem` 樣板參數的同義字。|  
|[int\_type](../Topic/basic_ios::int_type.md)|`Traits::int_type` 的同義字。|  
|[off\_type](../Topic/basic_ios::off_type.md)|`Traits::off_type` 的同義字。|  
|[pos\_type](../Topic/basic_ios::pos_type.md)|`Traits::pos_type` 的同義字。|  
|[traits\_type](../Topic/basic_ios::traits_type.md)|`Traits` 樣板參數的同義字。|  
  
### 成員函式  
  
|||  
|-|-|  
|[bad](../Topic/basic_ios::bad.md)|表示資料流緩衝區的完整性遺失。|  
|[清除](../Topic/basic_ios::clear.md)|清除所有錯誤的旗標。|  
|[copyfmt](../Topic/basic_ios::copyfmt.md)|將旗標從某個資料流複製到另一個資料流。|  
|[eof](../Topic/basic_ios::eof.md)|表示是否已到達資料流的結尾。|  
|[例外狀況](../Topic/basic_ios::exceptions.md)|表示此資料流會擲回哪些例外狀況。|  
|[fail](../Topic/basic_ios::fail.md)|表示無法從資料流擷取有效的欄位。|  
|[fill](../Topic/basic_ios::fill.md)|當此文字比該資料流還窄時，指定或傳回將要使用的字元。|  
|[good](../Topic/basic_ios::good.md)|表示資料流處於良好狀況。|  
|[imbue](../Topic/basic_ios::imbue.md)|變更地區設定。|  
|[init](../Topic/basic_ios::init.md)|由 `basic_ios` 建構函式所呼叫。|  
|[move](../Topic/basic_ios::move.md)|將所有值從此參數移動至目前物件，但該資料流緩衝區的指標除外。|  
|[narrow](../Topic/basic_ios::narrow.md)|尋找指定之 `char_type` 的對等字元。|  
|[rdbuf](../Topic/basic_ios::rdbuf.md)|將資料流路由轉送到指定緩衝區。|  
|[rdstate](../Topic/basic_ios::rdstate.md)|讀取旗標的位元狀態。|  
|[set\_rdbuf](../Topic/basic_ios::set_rdbuf.md)|指派此資料流緩衝區為此資料流物件的讀取緩衝區。|  
|[setstate](../Topic/basic_ios::setstate.md)|設定其他旗標。|  
|[交換](../Topic/basic_ios::swap.md)|用另一個 `basic_ios` 物件中的值交換這個 `basic_ios` 物件中的值。  不會交換資料流緩衝區的指標。|  
|[tie](../Topic/basic_ios::tie.md)|可確保一個資料流在另一個資料流之前先處理。|  
|[widen](../Topic/basic_ios::widen.md)|尋找指定字元的對等 `char_type`。|  
  
### 運算子  
  
|||  
|-|-|  
|[explicit operator bool](../Topic/basic_ios::operator%20bool.md)|允許使用 `basic_ios` 物件做為 `bool`。  自動類型轉換會停用，以避免常見非預期的副作用。|  
|[operator void \*](../Topic/basic_ios::operator%20void%20*.md)|表示資料流是否仍然良好。|  
|[operator\!](../Topic/basic_ios::operator!.md)|表示資料流是否沒有錯誤。|  
  
## 需求  
 **標頭：**\<ios\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)   
 [iostream 程式設計](../standard-library/iostream-programming.md)   
 [iostreams 慣例](../standard-library/iostreams-conventions.md)