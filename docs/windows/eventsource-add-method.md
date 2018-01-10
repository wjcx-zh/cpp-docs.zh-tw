---
title: "Eventsource:: Add 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::Add
dev_langs: C++
helpviewer_keywords: Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6e5a39abdced8929ac1a01db596a6099c70853c7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="eventsourceadd-method"></a>EventSource::Add 方法
附加事件處理常式所指定的委派介面代表目前的 EventSource 物件的事件處理常式的集合。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);  
```  
  
#### <a name="parameters"></a>參數  
 `delegateInterface`  
 要委派的物件，代表事件處理常式的介面。  
  
 `token`  
 這項作業完成時，代表事件的控制代碼。 當做參數，以使用此權杖[remove （)](../windows/eventsource-remove-method.md)捨棄事件處理常式方法。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>請參閱
 [EventSource 類別](../windows/eventsource-class.md)