---
title: "EventSource::addRemoveLock_ 資料成員 | Microsoft Docs"
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
  - "event/Microsoft::WRL::EventSource::addRemoveLock_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "addRemoveLock_ 資料成員"
ms.assetid: e2d69256-4891-4aad-ad0b-76479c0bb076
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::addRemoveLock_ 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

同步處理存取 [targets_](../windows/eventsource-targets-data-member.md) 陣列時加入、 移除或叫用事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
Wrappers::SRWLock addRemoveLock_;  
```  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)