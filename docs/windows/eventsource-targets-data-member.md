---
title: "EventSource::targets_ 資料成員 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::targets_"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "targets_ 資料成員"
ms.assetid: 5d5cee05-3315-4514-bce2-19173c923c7d
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::targets_ 資料成員
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

陣列的一個或多個事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
ComPtr<Details::EventTargetArray> targets_;  
```  
  
## <a name="remarks"></a>備註  
 當目前的 EventSource 物件由事件發生時，會呼叫事件處理常式。  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)