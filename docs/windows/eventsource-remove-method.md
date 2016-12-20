---
title: "EventSource::Remove 方法 | Microsoft Docs"
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
  - "event/Microsoft::WRL::EventSource::Remove"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Remove 方法"
ms.assetid: afafedf5-3665-4408-a639-fb6884f7c5f9
caps.latest.revision: 5
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# EventSource::Remove 方法
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

刪除從目前的 EventSource 物件相關聯的事件處理常式組指定的事件註冊語彙基元所表示的事件處理常式。  
  
## <a name="syntax"></a>語法  
  
```  
HRESULT Remove(  
   EventRegistrationToken token  
);  
```  
  
#### <a name="parameters"></a>參數  
 `token`  
 表示事件處理常式的控制代碼。 已註冊的事件處理常式時，傳回這個語彙基元 [add](../windows/eventsource-add-method.md) 方法。  
  
## <a name="return-value"></a>傳回值  
 如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。  
  
## <a name="remarks"></a>備註  
 如需 EventRegistrationToken 結構的詳細資訊，請參閱 Windows::Foundation::EventRegistrationToken 結構中的主題的 Windows 執行階段參考文件。  
  
## <a name="requirements"></a>需求  
 **標頭︰** event.h  
  
 **命名空間：** Microsoft::WRL
 
 ## <a name="see-also"></a>另請參閱
 [EventSource 類別](../windows/eventsource-class.md)