---
title: "accelerator_view 類別 | Microsoft Docs"
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
  - "amprt/Concurrency::accelerator_view"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "accelerator_view 類別"
ms.assetid: 9f298c21-bf62-46e0-88b8-01c5c78ef144
caps.latest.revision: 18
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# accelerator_view 類別
[!INCLUDE[vs2017banner](../../../assembler/inline/includes/vs2017banner.md)]

代表 C\+\+ AMP 資料平行加速器的虛擬裝置抽象層。  
  
## 語法  
  
```  
class accelerator_view;  
```  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view::accelerator\_view 建構函式](../Topic/accelerator_view::accelerator_view%20Constructor.md)|初始化 `accelerator_view` 類別的新執行個體。|  
|[accelerator\_view::~accelerator\_view 解構函式](../Topic/accelerator_view::~accelerator_view%20Destructor.md)|終結 `accelerator_view` 物件。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view::create\_marker 方法](../Topic/accelerator_view::create_marker%20Method.md)|傳回一個追蹤所有目前提交至此 `accelerator_view` 物件的命令的完成進度的 future 。|  
|[accelerator\_view::flush 方法](../Topic/accelerator_view::flush%20Method.md)|將所有暫停並佇列於 `accelerator_view` 物件的命令送出至加速器以執行。|  
|[accelerator\_view::get\_accelerator 方法](../Topic/accelerator_view::get_accelerator%20Method.md)|傳回 `accelerator_view` 物件的 `accelerator` 物件。|  
|[accelerator\_view::get\_is\_auto\_selection 方法](../Topic/accelerator_view::get_is_auto_selection%20Method.md)|傳回布林值，表示執行階段是否會在 `accelerator_view` 物件傳遞至 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 時，自動選取適當的加速器。|  
|[accelerator\_view::get\_is\_debug 方法](../Topic/accelerator_view::get_is_debug%20Method.md)|傳回代表 `accelerator_view` 物件是否具有在擴充錯誤報告啟用偵錯層級的布林 \(Boolean\) 值。|  
|[accelerator\_view::get\_queuing\_mode 方法](../Topic/accelerator_view::get_queuing_mode%20Method.md)|傳回 `accelerator_view` 物件的佇列模式。|  
|[accelerator\_view::get\_version 方法](../Topic/accelerator_view::get_version%20Method.md)|傳回`accelerator_view`的版本。|  
|[accelerator\_view::wait 方法](../Topic/accelerator_view::wait%20Method.md)|等候所有送出至 `accelerator_view` 物件的命令完成。|  
  
### 公用運算子  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view::operator\!\= 運算子](../Topic/accelerator_view::operator!=%20Operator.md)|將此 `accelerator_view` 物件與另一個相比較，如果相同則回傳 `false`，否則回傳 `true`。|  
|[accelerator\_view::operator\= 運算子](../Topic/accelerator_view::operator=%20Operator.md)|將指定之 `accelerator_view` 物件的內容複製到這個物件。|  
|[accelerator\_view::operator\=\= 運算子](../Topic/accelerator_view::operator==%20Operator.md)|將此 `accelerator_view` 物件與另一個相比較，如果相同則回傳 `true`，否則回傳 `false`。|  
  
### 公用資料成員  
  
|名稱|描述|  
|--------|--------|  
|[accelerator\_view::accelerator 資料成員](../Topic/accelerator_view::accelerator%20Data%20Member.md)|取得 `accelerator_view` 物件的 `accelerator` 物件。|  
|[accelerator\_view::is\_auto\_selection 資料成員](../Topic/accelerator_view::is_auto_selection%20Data%20Member.md)|取得布林值，表示執行階段是否會在 `accelerator_view` 物件傳遞至 [parallel\_for\_each](../Topic/parallel_for_each%20Function%20\(C++%20AMP\).md) 時，自動選取適當的加速器。|  
|[accelerator\_view::is\_debug 資料成員](../Topic/accelerator_view::is_debug%20Data%20Member.md)|取得布林值，表示 `accelerator_view` 物件是否針對大量錯誤報告啟用偵錯層。|  
|[accelerator\_view::queuing\_mode 資料成員](../Topic/accelerator_view::queuing_mode%20Data%20Member.md)|取得 `accelerator_view` 物件的佇列模式。|  
|[accelerator\_view::version 資料成員](../Topic/accelerator_view::version%20Data%20Member.md)|取得加速器版本。|  
  
## 繼承階層架構  
 `accelerator_view`  
  
## 備註  
 `accelerator_view` 物件表示加速器的邏輯隔離檢視。  單一實體計算裝置可以有多個邏輯、隔離 `accelerator_view` 物件。  每個加速器都有預設的 `accelerator_view` 物件。  可以建立其他 `accelerator_view` 物件。  
  
 實體裝置可以在許多用戶端執行緒共用。  用戶端執行緒可能是以合作方式使用加速器的相同 `accelerator_view` 物件，或者每個用戶端可以透過用來與其他用戶端執行緒隔離的獨立 `accelerator_view` 物件，與電腦裝置進行通訊。  
  
 `accelerator_view` 物件可以有兩個 [queuing\_mode 列舉](../../../parallel/amp/reference/queuing-mode-enumeration.md) 狀態中的其中一個狀態。  如果佇列的模式是 `immediate`，則像 `copy` 和 `parallel_for_each` 這樣的命令只要傳回給呼叫端，就會傳送至對應的加速器裝置。  如果佇列模式為 `deferred`，則這些命令會排入對應至 `accelerator_view` 物件的命令佇列。  在呼叫 `flush()` 以前，命令實際上都不會傳送至裝置。  
  
## 需求  
 **標頭：**amprt.h  
  
 **命名空間：**並行  
  
## 請參閱  
 [Concurrency 命名空間 \(C\+\+ AMP\)](../../../parallel/amp/reference/concurrency-namespace-cpp-amp.md)