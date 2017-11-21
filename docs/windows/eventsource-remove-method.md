---
title: "Eventsource:: Remove 方法 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: event/Microsoft::WRL::EventSource::Remove
dev_langs: C++
helpviewer_keywords: Remove method
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1879c939237275c279e1dd4bd1861ab3b02b468
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/24/2017
---
# <a name="eventsourceremove-method"></a>EventSource::Remove 方法
刪除指定的事件註冊語彙基元所代表與目前的 EventSource 物件相關聯的事件處理常式集合的事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>參數  
 `token`  
 代表事件處理常式的控制代碼。 註冊事件處理常式時，傳回這個語彙基元[add （)](../windows/eventsource-add-method.md)方法。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 如需詳細的 EventRegistrationToken 結構的詳細資訊，請參閱 Windows::Foundation::EventRegistrationToken 結構 > 主題中的 Windows 執行階段參考文件。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)