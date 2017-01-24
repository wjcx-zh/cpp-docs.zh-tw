---
title: "time_point 類別 | Microsoft Docs"
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
  - "chrono/std::chrono::time_point"
dev_langs: 
  - "C++"
ms.assetid: 18be1e52-57b9-489a-8a9b-f58894f0aaad
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# time_point 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

`time_point` 描述代表時間點的型別。  它保留[期間](../standard-library/duration-class.md)型別的物件，這個物件儲存從範本引數`Clock`所表示的時間開始所耗用時間。  
  
## 語法  
  
```  
template<  
   class Clock,  
   class Duration = typename Clock::duration  
>  
class time_point;  
```  
  
## 成員  
  
### 公用 Typedefs  
  
|Name|說明|  
|----------|--------|  
|`time_point::clock`|範本參數`Clock`的同義資料表。|  
|`time_point::duration`|範本參數`Duration`的同義資料表。|  
|`time_point::period`|巢狀型別名稱`duration::period`的同義資料表。|  
|`time_point::rep`|巢狀型別名稱`duration::rep`的同義資料表。|  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[time\_point::time\_point 建構函式](../Topic/time_point::time_point%20Constructor.md)|建構 `time_point` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[time\_point::max 方法](../Topic/time_point::max%20Method.md)|指定`time_point::ref`的上限。|  
|[time\_point::min 方法](../Topic/time_point::min%20Method.md)|指定 `time_point::ref`的下限。|  
|[time\_point::time\_since\_epoch 方法](../Topic/time_point::time_since_epoch%20Method.md)|傳回已儲存的 `duration` 值。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[time\_point::operator\+\= 運算子](../Topic/time_point::operator+=%20Operator.md)|將指定值加至儲存的期間。|  
|[time\_point::operator\-\= 運算子](../Topic/time_point::operator-=%20Operator.md)|從儲存的期間減去某個值。|  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)