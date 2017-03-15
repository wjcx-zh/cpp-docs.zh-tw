---
title: "EventSource::targetsPointerLock_ 資料成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::targetsPointerLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "targetsPointerLock_ 資料成員"
ms.assetid: 8f08409f-5262-4be7-9cf1-2ed15f19684a
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::targetsPointerLock_ 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步處理正在加入這個 EventSource 的事件處理常式、 同時也移除，或叫用的內部資料成員的存取權。  
  
## <a name="syntax"></a>語法  
  
```  
Wrappers::SRWLock targetsPointerLock_;  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)