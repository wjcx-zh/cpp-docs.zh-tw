---
title: AgileEventSource 類別 |Microsoft 文件
ms.custom: ''
ms.date: 03/22/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::AgileEventSource
- event/Microsoft::WRL::InvokeModeOptions
dev_langs:
- C++
helpviewer_keywords:
- AgileEventSource class
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d025fc2be86fb5b59107d1deee39962c3c6db04
ms.sourcegitcommit: 1d11412c8f5e6ddf4edded89e0ef5097cc89f812
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/22/2018
---
# <a name="agileeventsource-class"></a>AgileEventSource 類別
表示敏捷式軟體開發的事件。 繼承自[EventSource](eventsource-class.md)和覆寫`Add`成員函式，使用其他的型別參數來指定如何叫用事件敏捷式軟體開發的選項。
  
## <a name="syntax"></a>語法  
  
```  
template<typename TDelegateInterface, typename TEventSourceOptions = Microsoft::WRL::InvokeModeOptions<FireAll>>
class AgileEventSource
    : public Microsoft::WRL::EventSource<TDelegateInterface, TEventSourceOptions>;
```  
  
#### <a name="parameters"></a>參數  
 `TDelegateInterface`  
 要表示事件處理常式委派的介面。

 `TEventSourceOptions` [InvokeModeOptions](invokemodeoptions-structure.md) stucture 其 invokeMode 欄位設定為`InvokeMode::StopOnFirstError`或`InvokeMode::FireAll`。

## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[AgileEventSource::Add 方法](#add)|將附加敏捷式軟體開發的事件處理常式所指定的委派介面代表為目前 AgileEventSource 物件的事件處理常式的集合。|  

## <a name="add"></a> AgileEventSource::Add 方法

附加事件處理常式所指定的委派介面代表目前的 EventSource 物件的事件處理常式的集合。

### <a name="syntax"></a>語法

```cpp
HRESULT Add(  
   _In_ TDelegateInterface* delegateInterface,  
   _Out_ EventRegistrationToken* token  
);
```

### <a name="parameters"></a>參數

*delegateInterface*

要委派的物件，代表事件處理常式的介面。

*語彙基元*這項作業完成時，代表事件的控制代碼。 使用此權杖為 remove （） 方法的參數，捨棄此事件處理常式。

### <a name="return-value"></a>傳回值
如果作業成功，會傳送 S_OK；反之則傳送表示錯誤的 HRESULT 值。

## <a name="inheritance-hierarchy"></a>繼承階層  
 `EventSource`  
 `AgileEventSource`
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)