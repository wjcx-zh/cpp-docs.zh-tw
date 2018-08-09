---
title: EventTargetArray 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::Details::EventTargetArray
dev_langs:
- C++
helpviewer_keywords:
- EventTargetArray class
ms.assetid: e3cadb7c-2160-4cbb-a2f8-c28733d1e96d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 4cf5f885a002ede8a715eb4850eef5a8810a0309
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39648356"
---
# <a name="eventtargetarray-class"></a>EventTargetArray 類別
支援 WRL 結構，而且不是直接從您的程式碼使用。  
  
## <a name="syntax"></a>語法  
  
```cpp  
class EventTargetArray : public Microsoft::WRL::RuntimeClass<Microsoft::WRL::RuntimeClassFlags<ClassicCom>, IUnknown>;  
```  
  
## <a name="remarks"></a>備註  
 表示事件處理常式的陣列。  
  
 相關聯的事件處理常式[EventSource](../windows/eventsource-class.md)物件會儲存在受保護**EventTargetArray**資料成員。  
  
## <a name="members"></a>成員  
  
### <a name="public-constructors"></a>公用建構函式  
  
|名稱|描述|  
|----------|-----------------|  
|[EventTargetArray::EventTargetArray 建構函式](../windows/eventtargetarray-eventtargetarray-constructor.md)|初始化的新執行個體**EventTargetArray**類別。|  
|[EventTargetArray::~EventTargetArray 解構函式](../windows/eventtargetarray-tilde-eventtargetarray-destructor.md)|取消初始化目前**EventTargetArray**類別。|  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[EventTargetArray::AddTail 方法](../windows/eventtargetarray-addtail-method.md)|將指定的事件處理常式附加至事件處理常式內部陣列的結尾。|  
|[EventTargetArray::Begin 方法](../windows/eventtargetarray-begin-method.md)|取得內部陣列中的事件處理常式的第一個元素的位址。|  
|[EventTargetArray::End 方法](../windows/eventtargetarray-end-method.md)|取得內部陣列中的事件處理常式的最後一個元素的位址。|  
|[EventTargetArray::Length 方法](../windows/eventtargetarray-length-method.md)|取得目前的元素數目內部陣列中的事件處理常式。|  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `EventTargetArray`  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL::Details  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL::Details 命名空間](../windows/microsoft-wrl-details-namespace.md)