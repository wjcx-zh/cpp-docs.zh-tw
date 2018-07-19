---
title: CFirePropNotifyEvent 類別 |Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnChanged
- ATLCTL/ATL::CFirePropNotifyEvent::FireOnRequestEdit
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 20fd9c660f036c04ea2ca7d06d04315391504e3e
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/06/2018
ms.locfileid: "37881525"
---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 類別
這個類別提供方法來通知控制項屬性變更有關容器的接收器。  
  
> [!IMPORTANT]
>  此類別和其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|（靜態）通知容器接收已變更的控制項屬性。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|（靜態）通知控制項屬性即將變更的容器的接收器。|  
  
## <a name="remarks"></a>備註  
 `CFirePropNotifyEvent` 有兩種方法，通知控制項屬性已變更，或將變更容器的接收器。  
  
 如果實作您的控制項類別衍生自`IPropertyNotifySink`，則`CFirePropNotifyEvent`當您呼叫時，會叫用方法`FireOnRequestEdit`或`FireOnChanged`。 如果您的控制項類別不衍生自`IPropertyNotifySink`，這些函式的呼叫會傳回 S_OK。  
  
 如需建立控制項的詳細資訊，請參閱[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="fireonchanged"></a>  CFirePropNotifyEvent::FireOnChanged  
 告知所有已連接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) （在每個物件的連接點） 指定的物件屬性已變更的介面。  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標`IUnknown`傳送通知的物件。  
  
 *dispID*  
 [in]已變更之屬性的識別項。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此函式是安全地呼叫，即使您的控制項不支援連接點。  
  
##  <a name="fireonrequestedit"></a>  CFirePropNotifyEvent::FireOnRequestEdit  
 告知所有已連接[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) （在每個物件的連接點） 指定的物件屬性即將變更的介面。  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標`IUnknown`傳送通知的物件。  
  
 *dispID*  
 [in]若要變更之屬性的識別項。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準的 HRESULT 值。  
  
### <a name="remarks"></a>備註  
 此函式是安全地呼叫，即使您的控制項不支援連接點。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)
