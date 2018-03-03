---
title: "EventSource 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource
dev_langs:
- C++
helpviewer_keywords:
- EventSource class
ms.assetid: 91f1c072-6af4-44e6-b6d8-ac6d0c688dde
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 705260547d5a42b463d61b79c38592874f9dfa19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventsource-class"></a>EventSource 類別
表示事件。 EventSource 成員函式加入、 移除及叫用事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
template<  
   typename TDelegateInterface  
>  
class EventSource;  
```  
  
#### <a name="parameters"></a>參數  
 `TDelegateInterface`  
 要表示事件處理常式委派的介面。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[EventSource::EventSource 建構函式](../windows/eventsource-eventsource-constructor.md)|初始化 EventSource 類別的新執行個體。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[EventSource::Add 方法](../windows/eventsource-add-method.md)|附加事件處理常式所指定的委派介面代表目前的 EventSource 物件的事件處理常式的集合。|  
|[EventSource::GetSize 方法](../windows/eventsource-getsize-method.md)|擷取與目前的 EventSource 物件相關聯的事件處理常式的數目|  
|[EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)|使用指定的引數類型和引數目前的 EventSource 物件相關聯的每個事件處理常式會呼叫。|  
|[EventSource::Remove 方法](../windows/eventsource-remove-method.md)|刪除指定的事件註冊語彙基元所代表與目前的 EventSource 物件相關聯的事件處理常式集合的事件處理常式。|  
  
### <a name="protected-data-members"></a>受保護的資料成員  
  
|名稱|描述|  
|----------|-----------------|  
|[EventSource::addRemoveLock_ 資料成員](../windows/eventsource-addremovelock-data-member.md)|同步處理存取[targets_](../windows/eventsource-targets-data-member.md)陣列時加入、 移除或叫用事件處理常式。|  
|[EventSource::targets_ 資料成員](../windows/eventsource-targets-data-member.md)|陣列的一個或多個事件處理常式。|  
|[EventSource::targetsPointerLock_ 資料成員](../windows/eventsource-targetspointerlock-data-member.md)|加入事件處理常式，此 eventsource，同時也已移除，或叫用的內部資料成員的存取會同步處理。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `EventSource`  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)