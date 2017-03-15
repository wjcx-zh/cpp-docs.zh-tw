---
title: "EventSource::Add 方法 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "event/Microsoft::WRL::EventSource::Add"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Add 方法"
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
caps.latest.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# EventSource::Add 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

附加事件處理常式所指定的委派介面代表目前 EventSource 物件的事件處理常式的集合。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>參數  
 `delegateInterface`  
 要委派物件，表示事件處理常式的介面。  
  
 `token`  
 這項作業完成時，代表事件的控制代碼。 使用此權杖做為參數 [remove](../windows/eventsource-remove-method.md) 捨棄事件處理常式方法。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)