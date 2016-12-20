---
title: "moneypunct 類別 | Microsoft Docs"
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
  - "moneypunct"
  - "std.moneypunct"
  - "xlocmon/std::moneypunct"
  - "std::moneypunct"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "moneypunct 類別"
ms.assetid: cf2650da-3e6f-491c-95d5-23e57f582ee6
caps.latest.revision: 20
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# moneypunct 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以描述用來表示貨幣輸入欄位或貨幣輸出欄位之 `CharType` 類型的序列。  如果樣板參數 `Intl` 為 `true`，則遵守國際慣例。  
  
## 語法  
  
```  
template<class CharType, bool Intl>   
   class moneypunct;  
```  
  
#### 參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
 `Intl`  
 旗標，指定是否要遵守國際慣例。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。  第一次嘗試存取它的儲存值時，會在 **id** 中儲存唯一的正值。  
  
 常數靜態物件 intl 儲存樣板 **Intl** 的值。  
  
### 建構函式  
  
|||  
|-|-|  
|[moneypunct](../Topic/moneypunct::moneypunct.md)|`moneypunct` 類型物件的建構函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/moneypunct::char_type.md)|類型，用來描述由地區設定使用的字元。|  
|[string\_type](../Topic/moneypunct::string_type.md)|類型，描述包含 `CharType` 類型字元的字串。|  
  
### 成員函式  
  
|||  
|-|-|  
|[curr\_symbol](../Topic/moneypunct::curr_symbol.md)|傳回地區設定特定的項目序列，做為貨幣符號。|  
|[decimal\_point](../Topic/moneypunct::decimal_point.md)|傳回地區設定特定的項目序列，做為小數點符號。|  
|[do\_curr\_symbol](../Topic/moneypunct::do_curr_symbol.md)|受保護的虛擬成員函式，傳回地區設定特定的項目序列以做為貨幣符號。|  
|[do\_decimal\_point](../Topic/moneypunct::do_decimal_point.md)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為小數點符號。|  
|[do\_frac\_digits](../Topic/moneypunct::do_frac_digits.md)|受保護的虛擬成員函式傳回地區設定特定的小數點右邊位數。|  
|[do\_grouping](../Topic/moneypunct::do_grouping.md)|受保護的虛擬成員函式傳回決定如何將數字群組在小數點左側的地區設定特定規則。|  
|[do\_neg\_format](../Topic/moneypunct::do_neg_format.md)|受保護的虛擬成員函式，呼叫以傳回具有負數數量的格式化輸出的地區設定特定規則。|  
|[do\_negative\_sign](../Topic/moneypunct::do_negative_sign.md)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為負號。|  
|[do\_pos\_format](../Topic/moneypunct::do_pos_format.md)|受保護的虛擬成員函式，呼叫以傳回具有正數數量的格式化輸出的地區設定特定規則。|  
|[do\_positive\_sign](../Topic/moneypunct::do_positive_sign.md)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為正號。|  
|[do\_thousands\_sep](../Topic/moneypunct::do_thousands_sep.md)|受保護的虛擬成員函式，呼叫以傳回地區設定特定的項目序列，做為千位分隔符號。|  
|[frac\_digits](../Topic/moneypunct::frac_digits.md)|傳回地區設定特定的小數點右邊位數。|  
|[群組](../Topic/moneypunct::grouping.md)|傳回決定如何將數字群組在任何小數點左側的地區設定特定規則。|  
|[neg\_format](../Topic/moneypunct::neg_format.md)|傳回具有負數數量的格式化輸出的地區設定特定規則。|  
|[negative\_sign](../Topic/moneypunct::negative_sign.md)|傳回地區設定特定的項目序列，做為負號。|  
|[pos\_format](../Topic/moneypunct::pos_format.md)|傳回具有正數數量的格式化輸出的地區設定特定規則。|  
|[positive\_sign](../Topic/moneypunct::positive_sign.md)|傳回地區設定特定的項目序列，做為正號。|  
|[thousands\_sep](../Topic/moneypunct::thousands_sep.md)|傳回地區設定特定的項目序列，做為千位分隔符號。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)