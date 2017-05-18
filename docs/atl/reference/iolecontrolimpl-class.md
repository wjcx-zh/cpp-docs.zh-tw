---
title: "IOleControlImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleControlImpl
- ATLCTL/ATL::IOleControlImpl
- ATLCTL/ATL::IOleControlImpl::FreezeEvents
- ATLCTL/ATL::IOleControlImpl::GetControlInfo
- ATLCTL/ATL::IOleControlImpl::OnAmbientPropertyChange
- ATLCTL/ATL::IOleControlImpl::OnMnemonic
dev_langs:
- C++
helpviewer_keywords:
- IOleControlImpl class
ms.assetid: 5a4255ad-ede4-49ca-ba9a-07c2e919fa85
caps.latest.revision: 22
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 5e63849a504b931de30141dd91af557f16c67fd8
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="iolecontrolimpl-class"></a>IOleControlImpl 類別
這個類別提供的預設實作**IOleControl**介面和實作**IUnknown**。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class IOleControlImpl
```   
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleControlImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IOleControlImpl::FreezeEvents](#freezeevents)|指出容器忽略或接受來自控制項的事件。|  
|[IOleControlImpl::GetControlInfo](#getcontrolinfo)|填滿控制項的鍵盤行為的相關資訊。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleControlImpl::OnAmbientPropertyChange](#onambientpropertychange)|通知一或多個容器的環境屬性已變更的控制項。 ATL 實作會傳回`S_OK`。|  
|[IOleControlImpl::OnMnemonic](#onmnemonic)|通知控制項使用者已按下指定的按鍵。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 類別`IOleControlImpl`提供的預設實作[IOleControl](http://msdn.microsoft.com/library/windows/desktop/ms694320)介面和實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleControl`  
  
 `IOleControlImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="freezeevents"></a>IOleControlImpl::FreezeEvents  
 在 ATL 的實作中，`FreezeEvents`遞增 control 類別`m_nFreezeEvents`資料成員如果`bFreeze`是**TRUE**，並遞減`m_nFreezeEvents`如果`bFreeze`是**FALSE**。  
  
```
HRESULT FreezeEvents(BOOL bFreeze);
```  
  
### <a name="remarks"></a>備註  
 `FreezeEvents`然後傳回`S_OK`。  
  
 請參閱[IOleControl::FreezeEvents](http://msdn.microsoft.com/library/windows/desktop/ms678482)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getcontrolinfo"></a>IOleControlImpl::GetControlInfo  
 填滿控制項的鍵盤行為的相關資訊。  
  
```
HRESULT GetControlInfo(LPCONTROLINFO pCI);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleControl:GetControlInfo](http://msdn.microsoft.com/library/windows/desktop/ms693730)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
##  <a name="onambientpropertychange"></a>IOleControlImpl::OnAmbientPropertyChange  
 通知一或多個容器的環境屬性已變更的控制項。  
  
```
HRESULT OnAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleControl::OnAmbientPropertyChange](http://msdn.microsoft.com/library/windows/desktop/ms690175)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onmnemonic"></a>IOleControlImpl::OnMnemonic  
 通知控制項使用者已按下指定的按鍵。  
  
```
HRESULT OnMnemonic(LPMSG pMsg);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleControl::OnMnemonic](http://msdn.microsoft.com/library/windows/desktop/ms680699)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [IOleObjectImpl 類別](../../atl/reference/ioleobjectimpl-class.md)   
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [類別概觀](../../atl/atl-class-overview.md)

