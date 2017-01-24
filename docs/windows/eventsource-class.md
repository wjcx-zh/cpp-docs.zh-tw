---
title: "EventSource 類別 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "EventSource 類別"
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: 3
caps.handback.revision: 3
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource 類別
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

表示事件。  EventSource 成員函式新增，移除，並叫用事件處理常式。  
  
## 語法  
  
```  
template<  
   typename TDelegateInterface  
>  
class EventSource;  
```  
  
#### 參數  
 `TDelegateInterface`  
 對應的事件處理常式委派的介面。  
  
## Members  
  
### 公用建構函式  
  
|名稱|描述|  
|--------|--------|  
|[EventSource::EventSource 建構函式](../windows/eventsource-eventsource-constructor.md)|初始化 EventSource 類別的新執行個體。|  
  
### 公用方法  
  
|名稱|描述|  
|--------|--------|  
|[EventSource::Add 方法](../windows/eventsource-add-method.md)|將指定的委派介面所表示的事件處理常式加入至目前 EventSource 物件的事件處理常式。|  
|[EventSource::GetSize 方法](../windows/eventsource-getsize-method.md)|擷取與目前 EventSource 物件相關的事件處理常式數目|  
|[EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)|呼叫每一個與目前使用指定的引數型別和引數的 EventSource 物件相關的事件處理常式。|  
|[EventSource::Remove 方法](../windows/eventsource-remove-method.md)|刪除從一組指定的事件記錄檔的語彙基元所表示的事件處理常式的事件處理常式與目前 EventSource 物件。|  
  
### 受保護的資料成員  
  
|名稱|描述|  
|--------|--------|  
|[EventSource::addRemoveLock\_ 資料成員](../windows/eventsource-addremovelock-data-member.md)|當加入、移除，或叫用事件處理常式時，同步處理對 [targets\_](../windows/eventsource-targets-data-member.md) 陣列的存取。|  
|[EventSource::targets\_ 資料成員](../windows/eventsource-targets-data-member.md)|一個或多個事件處理常式的陣列。|  
|[EventSource::targetsPointerLock\_ 資料成員](../windows/eventsource-targetspointerlock-data-member.md)|甚至，當這個 EventSource 的事件處理常式中，加入、移除或叫用時，同步處理至內部資料成員的存取。|  
  
## 繼承階層架構  
 `EventSource`  
  
## 需求  
 **標題:** event.h  
  
 **命名空間：**Microsoft::WRL  
  
## 請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)