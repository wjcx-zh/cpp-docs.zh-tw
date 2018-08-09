---
title: 'Eventsource:: Remove 方法 |Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::EventSource::Remove
dev_langs:
- C++
helpviewer_keywords:
- Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 36a057bbad39e61576828c5a02f6863248b235cf
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641401"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 方法
刪除從目前與相關聯的事件處理常式的集合指定的事件註冊語彙基元所代表的事件處理常式**EventSource**物件。  
  
## <a name="syntax"></a>語法  
  
```cpp  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
### <a name="parameters"></a>參數  
 *語彙基元*  
 代表事件處理常式的控制代碼。 註冊事件處理常式時，傳回這個語彙基元[add （)](../windows/eventsource-add-method.md)方法。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 如需詳細資訊`EventRegistrationToken`結構，請參閱**Windows::Foundation::EventRegistrationToken 結構**中的主題**Windows 執行階段**參考文件。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)