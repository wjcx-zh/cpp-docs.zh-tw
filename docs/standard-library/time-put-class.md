---
title: "time_put 類別 | Microsoft Docs"
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
  - "std::time_put"
  - "time_put"
  - "xloctime/std::time_put"
  - "std.time_put"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "time_put 類別"
ms.assetid: df79493e-3331-48d2-97c3-ac3a745f0791
caps.latest.revision: 22
caps.handback.revision: 12
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_put 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

此樣板類別描述可以做為地區設定 facet 的物件，以控制時間值轉換為類型 `CharType` 的序列。  
  
## 語法  
  
```  
template <  
   class CharType,  
   class OutputIterator = ostreambuf_iterator<CharType>  
> class time_put : public locale::facet;  
```  
  
#### 參數  
 `CharType`  
 用於程式內部字元編碼的類型。  
  
 `OutputIterator`  
 時間 put 函式將其輸出寫入其中的迭代器類型。  
  
## 備註  
 如同所有地區設定 facet，靜態物件識別碼有初始儲存值零。  第一次嘗試存取它的儲存值時，會在 **id** 中儲存唯一的正值。  
  
### 建構函式  
  
|||  
|-|-|  
|[time\_put](../Topic/time_put::time_put.md)|`time_put` 類型物件的建構函式。|  
  
### Typedef  
  
|||  
|-|-|  
|[char\_type](../Topic/time_put::char_type.md)|類型，用來描述由地區設定使用的字元。|  
|[iter\_type](../Topic/time_put::iter_type.md)|描述輸出迭代器的類型。|  
  
### 成員函式  
  
|||  
|-|-|  
|[do\_put](../Topic/time_put::do_put.md)|虛擬函式，會輸出日期和時間資訊做為 `CharType` 的序列。|  
|[put](../Topic/time_put::put.md)|輸出日期和時間資訊做為 `CharType` 的序列。|  
  
## 需求  
 **標頭：**\<locale\>  
  
 **命名空間:** std  
  
## 請參閱  
 [\<locale\>](../standard-library/locale.md)   
 [time\_base 類別](../standard-library/time-base-class.md)   
 [C\+\+ 標準程式庫中的執行緒安全](../standard-library/thread-safety-in-the-cpp-standard-library.md)