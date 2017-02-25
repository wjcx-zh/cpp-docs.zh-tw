---
title: "time_get 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "std.time_get"
  - "xloctime/std::time_get"
  - "time_get"
  - "std::time_get"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_get 類別"
ms.assetid: 869d5f5b-dbab-4628-8333-bdea7e272023
caps.latest.revision: 21
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 21
---
# time_get 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以控制類型 `CharType` 的序列轉換為時間值。  
  
## 語法  
  
```  
template <  
   class CharType,  
   class InputIterator = istreambuf_iterator<CharType>  
> class time_get : public time_base;  
```  
  
#### 參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
 `InputIterator`  
 從中讀取時間值的迭代器。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。  第一次嘗試存取它的儲存值時，會在 **id** 中儲存唯一的正值。  
  
### 建構函式  
  
|||  
|-|-|  
|[time\_get](../Topic/time_get::time_get.md)|`time_get` 類型物件的建構函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/time_get::char_type.md)|類型，用來描述由地區設定使用的字元。|  
|[iter\_type](../Topic/time_get::iter_type.md)|描述輸入迭代器的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[date\_order](../Topic/time_get::date_order.md)|傳回 facet 使用的日期順序。|  
|[do\_date\_order](../Topic/time_get::do_date_order.md)|受保護的虛擬成員函式，呼叫以傳回 facet 所使用的日期順序。|  
|[do\_get](../Topic/time_get::do_get.md)|讀取和轉換字元資料為時間值。|  
|[do\_get\_date](../Topic/time_get::do_get_date.md)|受保護的虛擬成員函式，呼叫以將字串剖析為由 `strftime` 的 `x` 規範所產生的日期。|  
|[do\_get\_monthname](../Topic/time_get::do_get_monthname.md)|受保護的虛擬成員函式，呼叫以將字串剖析為月份名稱。|  
|[do\_get\_time](../Topic/time_get::do_get_time.md)|受保護的虛擬成員函式，呼叫以將字串剖析為由 `strftime` 的 `X` 規範所產生的日期。|  
|[do\_get\_weekday](../Topic/time_get::do_get_weekday.md)|受保護的虛擬成員函式，呼叫以將字串剖析為週間日名稱。|  
|[do\_get\_year](../Topic/time_get::do_get_year.md)|受保護的虛擬成員函式，呼叫以將字串剖析為年份名稱。|  
|[get](../Topic/time_get::get.md)|從字元資料來源讀取，並將該資料轉換為時間結構儲存的時間。|  
|[get\_date](../Topic/time_get::get_date.md)|將字串剖析為 `strftime` 的 `x` 規範所產生的日期。|  
|[get\_monthname](../Topic/time_get::get_monthname.md)|將字串剖析為月份名稱。|  
|[get\_time](../Topic/time_get::get_time.md)|將字串剖析為 `strftime` 的 `X` 規範所產生的日期。|  
|[get\_weekday](../Topic/time_get::get_weekday.md)|將字串剖析為週間日名稱。|  
|[get\_year](../Topic/time_get::get_year.md)|將字串剖析為年份名稱。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base 類別](../standard-library/time-base-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)