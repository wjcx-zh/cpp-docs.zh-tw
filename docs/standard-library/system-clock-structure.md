---
title: "system_clock 結構 | Microsoft Docs"
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
  - "chrono/std::chrono::system_clock"
dev_langs: 
  - "C++"
ms.assetid: a97bd46e-267a-4836-9f7d-af1f664e99ae
caps.latest.revision: 14
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# system_clock 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表以系統的即時時鐘為基礎的*計時類型*。  
  
## 語法  
  
```  
struct system_clock;  
```  
  
## 備註  
 *計時類型*用來取得目前的 UTC 時間。  此類型具現化 [duration](../standard-library/duration-class.md) 和類別樣板 [time\_point](../standard-library/time-point-class.md)，並定義可傳回時間的靜態成員函式 `now()`。  
  
 如果第一次呼叫 `now()` 傳回的值一律小於或等於後續呼叫 `now()` 所傳回的值，則時鐘具「*單一性*」。  
  
 如果時鐘具「*單一性*」且時鐘刻度之間的時間固定，則時鐘具「*穩定性*」。  
  
 在此實作中，`system_clock` 與 `high_resolution_clock` 同義。  
  
## 成員  
  
### 公用 Typedefs  
  
|名稱|描述|  
|--------|--------|  
|`system_clock::duration`|`duration<rep, period>` 的同義字。|  
|`system_clock::period`|與內含具現化 `duration` 時用來代表刻度期間的類型是同義字。|  
|`system_clock::rep`|與 `duration` 內含具現化時用來代表時鐘刻度數目的類型是同義字。|  
|`system_clock::time_point`|`time_point<Clock, duration>` 的同義字，其中 `Clock` 是計時類型本身的同義字，或與另一種根據相同 Epoch 且有相同巢狀 `duration` 類型的計時類型是同義字。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[system\_clock::from\_time\_t 方法](../Topic/system_clock::from_time_t%20Method.md)|靜態。  傳回最接近指定時間的 `time_point`。|  
|[system\_clock::now 方法](../Topic/system_clock::now%20Method.md)|靜態。  傳回目前時間。|  
|[system\_clock::to\_time\_t 方法](../Topic/system_clock::to_time_t%20Method.md)|靜態。  傳回最接近指定 `time_point` 的 `time_t` 物件。|  
  
### 公用常數  
  
|名稱|描述|  
|--------|--------|  
|[system\_clock::is\_monotonic 常數](../Topic/system_clock::is_monotonic%20Constant.md)|指定計時類型是否具單調性。|  
|[system\_clock::is\_steady 常數](../Topic/system_clock::is_steady%20Constant.md)|指定計時類型是否具穩定性。|  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [steady\_clock 結構](../standard-library/steady-clock-struct.md)