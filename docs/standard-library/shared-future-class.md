---
title: "shared_future 類別 | Microsoft Docs"
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
  - "future/std::shared_future"
dev_langs: 
  - "C++"
ms.assetid: 454ebedd-f42b-405f-99a5-a25cc9ad7c90
caps.latest.revision: 13
caps.handback.revision: 3
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# shared_future 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

描述非同步 *傳回物件*。  與 [未來](../standard-library/future-class.md) 物件相比，非同步 *提供者* 可以與任何數目的 `shared_future` 物件。  
  
## 語法  
  
```  
template<class Ty>  
class shared_future;  
```  
  
## 備註  
 不要呼叫任何方法刪除 `valid`、 `operator=`和解構函式外為 *空白的*`shared_future` 物件。  
  
 `shared_future` 物件不是同步化的。  呼叫相同物件的方法從多個執行緒引入有無法預期的結果的資料會符合。  
  
## 成員  
  
### 公用建構函式  
  
|Name|說明|  
|----------|--------|  
|[shared\_future::shared\_future 建構函式](../Topic/shared_future::shared_future%20Constructor.md)|建構 `shared_future` 物件。|  
  
### 公用方法  
  
|Name|說明|  
|----------|--------|  
|[shared\_future::get 方法](../Topic/shared_future::get%20Method.md)|擷取與這個 *相關聯的非同步狀態*儲存在本機的結果。|  
|[shared\_future::valid 方法](../Topic/shared_future::valid%20Method.md)|指定物件是否不是空的。|  
|[shared\_future::wait 方法](../Topic/shared_future::wait%20Method.md)|封鎖目前的執行緒，直到此關聯的非同步狀態為就緒。|  
|[shared\_future::wait\_for 方法](../Topic/shared_future::wait_for%20Method.md)|在這個關聯的非同步狀態的區塊準備好或在指定的時間長度已經過去。|  
|[shared\_future::wait\_until 方法](../Topic/shared_future::wait_until%20Method.md)|在這個關聯的非同步狀態的區塊準備好或在指定的時間點。|  
  
### 公用運算子  
  
|Name|說明|  
|----------|--------|  
|[shared\_future::operator\= 運算子](../Topic/shared_future::operator=%20Operator.md)|將新的相關聯的非同步狀態。|  
  
## 需求  
 **標題:** future  
  
 **命名空間:** std  
  
## 請參閱  
 [標頭檔參考](../standard-library/cpp-standard-library-header-files.md)   
 [\<future\>](../standard-library/future.md)