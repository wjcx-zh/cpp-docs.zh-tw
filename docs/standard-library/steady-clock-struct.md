---
title: "steady_clock 結構 | Microsoft Docs"
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
  - "chrono/std::chrono::steady_clock"
dev_langs: 
  - "C++"
ms.assetid: 970d12ec-fc80-4391-a2f7-b57b2aec668d
caps.latest.revision: 14
caps.handback.revision: 5
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# steady_clock 結構
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

代表 `steady` 時鐘。  
  
## 語法  
  
```  
struct steady_clock;  
```  
  
## 備註  
 在 Windows 中，steady\_clock 會包裝 QueryPerformanceCounter 函式。  
  
 如果第一次呼叫 `now()` 傳回的值一律小於或等於後續呼叫 `now()` 所傳回的值，則時鐘具「*單一性*」。  
  
 如果時鐘具「*單一性*」且時鐘刻度之間的時間固定，則時鐘具「*穩定性*」。  
  
 High\_resolution\_clock 是 steady\_clock 的 typdef。  
  
## 公用函式  
  
|函式|描述|  
|--------|--------|  
|now|傳回目前的時間做為 time\_point 值。|  
  
## 公用常數  
  
|名稱|描述|  
|--------|--------|  
|`system_clock::is_steady`|保有 `true` `steady_clock` 為 *steady*。|  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [system\_clock 結構](../standard-library/system-clock-structure.md)