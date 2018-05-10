---
title: 'Eventsource:: Add 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Add
dev_langs:
- C++
helpviewer_keywords:
- Add method
ms.assetid: 8bded85b-929e-4425-a464-e5de67bb774c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92af8746b4d2b5ba2f379cc8660b5345b2c5f175
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
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
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)