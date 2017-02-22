---
title: "progress_reporter 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "ppltasks/concurrency::progress_reporter"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "progress_reporter 類別"
ms.assetid: b836efab-2d05-4649-b6fa-d15236f1f813
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 11
---
# progress_reporter 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

進度報告者類別允許報告特定類型的進度通知。  每個 progress\_reporter 物件都會繫結至特定非同步動作或作業。  
  
## 語法  
  
```  
template<  
   typename _ProgressType  
>  
class progress_reporter;  
```  
  
#### 參數  
 `_ProgressType`  
 透過進度報告者所報告，每個進度通知的承載類型。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[progress\_reporter::progress\_reporter 建構函式](../Topic/progress_reporter::progress_reporter%20Constructor.md)||  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[progress\_reporter::report 方法](../Topic/progress_reporter::report%20Method.md)|將進度報告傳送至這個進度報告者已繫結的非同步動作或作業。|  
  
## 備註  
 這個類型只供 Windows 市集應用程式使用。  
  
## 繼承階層架構  
 `progress_reporter`  
  
## 需求  
 **標頭：**ppltasks.h  
  
 **命名空間：**concurrency  
  
## 請參閱  
 [concurrency 命名空間](../../../parallel/concrt/reference/concurrency-namespace.md)   
 [create\_async 函式](../Topic/create_async%20Function.md)