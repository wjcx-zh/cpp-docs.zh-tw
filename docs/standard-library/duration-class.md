---
title: "duration 類別 | Microsoft Docs"
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
  - "chrono/std::chrono::duration"
dev_langs: 
  - "C++"
ms.assetid: 06b863b3-65be-4ded-a72e-6e1eb1531077
caps.latest.revision: 10
caps.handback.revision: 4
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# duration 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述保留 *時間間隔*的型別，而時間間隔是指在兩個時間點之間所耗用的時間。  
  
## 語法  
  
```  
template<  
   class Rep,  
   class Period = ratio<1>  
>  
class duration;  
template<  
   class Rep,  
   class Period  
>  
class duration;  
template<  
   class Rep,  
   class Period1,  
   class Period2  
>  
class duration  
   <duration<Rep, Period1>, Period2>;  
```  
  
## 備註  
 樣板引數 `Rep` 描述用來保存時脈週期數間隔的型別。  樣板引數 `Period` 是[比率](../standard-library/ratio.md) 的實例，其描述每刻度所表示的間隔大小。  
  
## 成員  
  
### 公用 Typedefs  
  
|Name|說明|  
|----------|--------|  
|[duration::period Typedef](http://msdn.microsoft.com/zh-tw/ebf2a1b9-769f-475f-8c66-cf9ed12015f2)|代表範本參數 `Period`之同義資料表。|  
|[duration::rep Typedef](http://msdn.microsoft.com/zh-tw/f47b8abb-ae2c-4dc8-858a-f44695156950)|代表範本參數 `Rep`之同義資料表。|  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[duration::duration 建構函式](../Topic/duration::duration%20Constructor.md)|建構 `duration` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[duration::count 方法](../Topic/duration::count%20Method.md)|回傳時間間隔的時鐘刻度數。|  
|[duration::max 方法](../Topic/duration::max%20Method.md)|靜態。  回傳範本參數 `Ref`的最大容許值。|  
|[duration::min 方法](../Topic/duration::min%20Method.md)|靜態。  回傳範本參數 `Ref`的最低容許值。|  
|[duration::zero 方法](../Topic/duration::zero%20Method.md)|靜態。  實際上，傳回 `Rep`\(0\)。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[duration::operator\- 運算子](../Topic/duration::operator-%20Operator.md)|與相反的滴答計數一起傳回 `duration` 物件的複本。|  
|[duration::operator\-\- 運算子](../Topic/duration::operator--%20Operator.md)|減少已儲存的滴答計數。|  
|[duration::operator\= 運算子](../Topic/duration::operator=%20Operator.md)|取儲存的滴答計數對某個指定值的模數。|  
|[duration::operator\*\= 運算子](../Topic/duration::operator*=%20Operator.md)|將已儲存的滴答計數乘以某個指定值。|  
|[duration::operator\/\= 運算子](../Topic/duration::operator-=%20Operator1.md)|已儲存的滴答計數除以指定之 `duration` 物件的滴答計數。|  
|[duration::operator\+ 運算子](../Topic/duration::operator+%20Operator.md)|傳回 `*this`。|  
|[duration::operator\+\+ 運算子](../Topic/duration::operator++%20Operator.md)|增加已儲存的滴答計數。|  
|[duration::operator\+\= 運算子](../Topic/duration::operator+=%20Operator.md)|將指定之 `duration` 物件的滴答計數增加至已儲存的滴答計數。|  
|[duration::operator\-\= 運算子](../Topic/duration::operator-=%20Operator2.md)|從已儲存的滴答計數扣除指定之 `duration` 物件的滴答計數。|  
  
## 需求  
 **標頭：**chrono  
  
 **命名空間：**std::chrono  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<chrono\>](../standard-library/chrono.md)   
 [duration\_values 結構](../standard-library/duration-values-structure.md)