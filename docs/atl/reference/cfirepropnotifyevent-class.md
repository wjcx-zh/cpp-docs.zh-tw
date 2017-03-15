---
title: "CFirePropNotifyEvent 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CFirePropNotifyEvent
- ATL::CFirePropNotifyEvent
- ATL.CFirePropNotifyEvent
dev_langs:
- C++
helpviewer_keywords:
- sinks, notifying of ATL events
- CFirePropNotifyEvent class
- connection points [C++], notifying of events
ms.assetid: eb7a563e-6bce-4cdf-8d20-8c6a5307781b
caps.latest.revision: 20
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 1511a9e9ba287d12aade7c393887c6b5f8880b96
ms.lasthandoff: 02/24/2017

---
# <a name="cfirepropnotifyevent-class"></a>CFirePropNotifyEvent 類別
這個類別提供方法來通知有關控制項的屬性變更容器的接收器。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
class CFirePropNotifyEvent
```  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[CFirePropNotifyEvent::FireOnChanged](#fireonchanged)|（靜態）通知容器接收已變更的控制項屬性。|  
|[CFirePropNotifyEvent::FireOnRequestEdit](#fireonrequestedit)|（靜態）通知即將變更的控制項屬性的容器的接收器。|  
  
## <a name="remarks"></a>備註  
 `CFirePropNotifyEvent`有兩種方法，通知的控制項屬性已變更，或將變更容器的接收器。  
  
 如果實作控制項的類別衍生自`IPropertyNotifySink`、`CFirePropNotifyEvent`方法叫用，當您呼叫`FireOnRequestEdit`或`FireOnChanged`。 如果您的控制項類別不衍生自`IPropertyNotifySink`，這些函式呼叫會傳回`S_OK`。  
  
 如需有關如何建立控制項的詳細資訊，請參閱[ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)。  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="a-namefireonchangeda--cfirepropnotifyeventfireonchanged"></a><a name="fireonchanged"></a>CFirePropNotifyEvent::FireOnChanged  
 通知所有連線[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) （在每個物件的連接點） 上指定的物件屬性已變更的介面。  
  
```
static HRESULT FireOnChanged(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**傳送通知的物件。  
  
 *dispID*  
 [in]已變更之屬性的識別項。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 此函式是安全地呼叫，即使您的控制項不支援連接點。  
  
##  <a name="a-namefireonrequestedita--cfirepropnotifyeventfireonrequestedit"></a><a name="fireonrequestedit"></a>CFirePropNotifyEvent::FireOnRequestEdit  
 通知所有連線[IPropertyNotifySink](http://msdn.microsoft.com/library/windows/desktop/ms692638) （在每個物件的連接點） 上指定的物件屬性即將變更的介面。  
  
```
static HRESULT FireOnRequestEdit(IUnknown* pUnk, DISPID dispID);
```  
  
### <a name="parameters"></a>參數  
 *pUnk*  
 [in]指標**IUnknown**傳送通知的物件。  
  
 *dispID*  
 [in]若要變更之屬性的識別碼。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 此函式是安全地呼叫，即使您的控制項不支援連接點。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

