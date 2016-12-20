---
title: "char_traits 結構 | Microsoft Docs"
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
  - "std::char_traits"
  - "std.char_traits"
  - "iosfwd/std::char_traits"
  - "char_traits"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "char_traits 類別"
  - "char_traits 結構"
ms.assetid: 568e59f0-4521-4207-9223-9dcf6a16d620
caps.latest.revision: 20
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# char_traits 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Char\_traits 結構會描述與字元相關聯的屬性。  
  
## 語法  
  
```  
template <  
   class CharType  
> struct char_traits;  
```  
  
#### 參數  
 `CharType`  
 項目資料類型。  
  
## 備註  
 此範本結構描述 **CharType** 類型的不同字元特性。  此範本類別 [basic\_string](../standard-library/basic-string-class.md) 以及數個 iostream 範本類別 \(包含 [basic\_ios](../standard-library/basic-ios-class.md)\) 會使用此資訊來管理 **CharType** 類型的項目。  這類項目類型不得要求明確建構或解構。  它必須將預設建構函式、複製建構函式和指派運算子提供給預期的語意。  位元複製必須具有和指派相同的效果。  結構 char\_traits 的成員函式都無法擲回例外狀況。  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/char_traits::char_type.md)|字元的類型。|  
|[int\_type](../Topic/char_traits::int_type.md)|整數類型，可以代表 `char_type` 類型的字元或檔案結尾 \(EOF\) 字元。|  
|[off\_type](../Topic/char_traits::off_type.md)|整數類型，可以代表資料流中位置之間的位移。|  
|[pos\_type](../Topic/char_traits::pos_type.md)|整數類型，可以代表資料流中的位置。|  
|[state\_type](../Topic/char_traits::state_type.md)|類型，代表資料流中多位元組字元的轉換狀態。|  
  
### 成員函式  
  
|||  
|-|-|  
|[assign](../Topic/char_traits::assign.md)|將一個字元的值指派給另一個。|  
|[compare](../Topic/char_traits::compare.md)|比較多達兩個字串中字元的指定數目。|  
|[copy](../Topic/char_traits::copy.md)|將指定的字元數從一個字串複製到另一個。  已取代。  請改用 [char\_traits::\_Copy\_s](../Topic/char_traits::_Copy_s.md)。|  
|[\_Copy\_s](../Topic/char_traits::_Copy_s.md)|將指定的字元數從一個字串複製到另一個。|  
|[eof](../Topic/char_traits::eof.md)|傳回檔案結尾 \(EOF\) 字元。|  
|[eq](../Topic/char_traits::eq.md)|測試兩個 `char_type` 字元是否相等。|  
|[eq\_int\_type](../Topic/char_traits::eq_int_type.md)|測試兩個表示為 `int_type` 的字元是否相等。|  
|[find](../Topic/char_traits::find.md)|在字元範圍中搜尋指定字元第一次出現處。|  
|[長度](../Topic/char_traits::length.md)|傳回字串的長度。|  
|[lt](../Topic/char_traits::lt.md)|測試一個字元是否小於另一個。|  
|[move](../Topic/char_traits::move.md)|將序列中指定的字元數複製到可能重疊的另一個序列。  已取代。  請改用 [char\_traits::\_Move\_s](../Topic/char_traits::_Move_s.md)。|  
|[\_Move\_s](../Topic/char_traits::_Move_s.md)|將序列中指定的字元數複製到可能重疊的另一個序列。|  
|[not\_eof](../Topic/char_traits::not_eof.md)|測試字元是否為檔案結尾 \(EOF\) 字元。|  
|[to\_char\_type](../Topic/char_traits::to_char_type.md)|將 `int_type` 字元轉換為對應的 `char_type` 字元，並傳回結果。|  
|[to\_int\_type](../Topic/char_traits::to_int_type.md)|將 `char_type` 字元轉換為對應的 `int_type` 字元，並傳回結果。|  
  
## 需求  
 **標頭：**\<string\>  
  
 **命名空間:** std  
  
## 請參閱  
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)