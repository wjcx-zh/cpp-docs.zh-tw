---
title: 'Deferrableeventargs:: Invokeallfinished 方法 |Microsoft 文件'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 86b45205-3edb-4134-9cd0-ed7a7b4c3b1a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1aaaf8c6849b30e26463810ff353234319960048
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/08/2018
---
# <a name="deferrableeventargsinvokeallfinished-method"></a>DeferrableEventArgs::InvokeAllFinished 方法
呼叫此方法，表示已完成延期事件的所有處理。  
  
## <a name="syntax"></a>語法  
  
```cpp  
void InvokeAllFinished()  
```  
  
## <a name="remarks"></a>備註  
 您應該呼叫這個方法之後的事件來源呼叫[InvokeAll](../windows/eventsource-invokeall-method.md)。 呼叫這個方法能避免其他延期，並在沒有採取任何延期時，強制執行完成處理常式。  
  
 如需程式碼範例，請參閱[DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [DeferrableEventArgs 類別](../windows/deferrableeventargs-class.md)   
 [EventSource::InvokeAll 方法](../windows/eventsource-invokeall-method.md)