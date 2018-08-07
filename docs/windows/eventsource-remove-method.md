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
ms.openlocfilehash: 9dd026158a2bbc76e7a3e195bc5346f65821f2b7
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/06/2018
ms.locfileid: "39569491"
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 方法
刪除從目前與相關聯的事件處理常式的集合指定的事件註冊語彙基元所代表的事件處理常式**EventSource**物件。  
  
## <a name="syntax"></a>語法  
  
```  
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
 如需詳細的 EventRegistrationToken 結構的詳細資訊，請參閱`Windows::Foundation::EventRegistrationToken`結構 Windows 執行階段參考文件中的主題。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)