---
title: DeferrableEventArgs 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: ece89267-7b72-40e1-8185-550c865b070a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8dd9452133267021effd307734b5c5cf55922720
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/08/2018
ms.locfileid: "39642298"
---
# <a name="deferrableeventargs-class"></a>DeferrableEventArgs 類別
範本類別，用於延期的事件引數類型。  
  
## <a name="syntax"></a>語法  
  
```cpp  
template <  
typename TEventArgsInterface,  
typename TEventArgsClass  
>  
class DeferrableEventArgs : public TEventArgsInterface  
```  
  
### <a name="parameters"></a>參數  
 *TEventArgsInterface*  
 宣告延期事件之引數的介面類別。  
  
 *TEventArgsClass*  
 此類別可實作*TEventArgsInterface*。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[DeferrableEventArgs::GetDeferral 方法](../windows/deferrableeventargs-getdeferral-method.md)|取得參考[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)代表延期的事件的物件。|  
|[DeferrableEventArgs::InvokeAllFinished 方法](../windows/deferrableeventargs-invokeallfinished-method.md)|呼叫此方法，表示已完成延期事件的所有處理。|  
  
## <a name="remarks"></a>備註  
 這個類別的執行個體會傳遞至延期事件的事件處理常式。 範本參數代表定義延期事件特定類型之事件引數詳細資料的介面，以及實作該介面的類別。  
  
 此類別會顯示為延期事件之事件處理常式的第一個引數。 您可以呼叫[GetDeferral](../windows/deferrableeventargs-getdeferral-method.md)方法來取得[延遲](http://go.microsoft.com/fwlink/p/?linkid=526520)從中中，您可以取得有關延期事件的所有資訊的物件。 完成事件處理之後，您應該在延期物件上呼叫 Complete。 您應該都會接著呼叫[InvokeAllFinished](../windows/deferrableeventargs-invokeallfinished-method.md)結尾的事件處理常式方法，以確保所有延期事件的完成都正確通訊。  
  
## <a name="requirements"></a>需求  
 **標頭：** event.h  
  
 **命名空間：** Microsoft::WRL  
  
## <a name="see-also"></a>另請參閱  
 [Microsoft::WRL 命名空間](../windows/microsoft-wrl-namespace.md)