---
title: "IPointerInactiveImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IPointerInactiveImpl
dev_langs:
- C++
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
caps.latest.revision: 21
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 05cf4b2247cabe713cfc6b0dd54c95c01e5bbddc
ms.lasthandoff: 02/24/2017

---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl 類別
這個類別會實作**IUnknown**和[IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)介面方法。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class IPointerInactiveImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IPointerInactiveImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|擷取物件目前的啟用原則。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|將滑鼠指標移過它，表示物件的物件可以引發滑鼠事件的通知。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|設定滑鼠指標為非作用中的物件。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 非作用中的物件就是只要載入或執行。 不同於作用中的物件，非作用中的物件無法接收 Windows 滑鼠和鍵盤訊息。 因此，非作用中的物件會使用較少的資源，通常更有效率。  
  
 [IPointerInactive](http://msdn.microsoft.com/library/windows/desktop/ms693712)介面可讓物件，以支援滑鼠互動，同時仍然作用中的最低層級。 這項功能是特別有用的控制項。  
  
 類別`IPointerInactiveImpl`實作`IPointerInactive`方法藉由直接傳回**E_NOTIMPL**。 不過，它會實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IPointerInactive`  
  
 `IPointerInactiveImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="a-namegetactivationpolicya--ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy  
 擷取物件目前的啟用原則。  
  
```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPointerInactive::GetActivationPolicy](http://msdn.microsoft.com/library/windows/desktop/ms692470)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoninactivemousemovea--ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove  
 將滑鼠指標移過它，表示物件的物件可以引發滑鼠事件的通知。  
  
```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPointerInactive::OnInactiveMouseMove](http://msdn.microsoft.com/library/windows/desktop/ms693374)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameoninactivesetcursora--ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor  
 設定滑鼠指標為非作用中的物件。  
  
```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IPointerInactive::OnInactiveSetCursor](http://msdn.microsoft.com/library/windows/desktop/ms694336)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [類別概觀](../../atl/atl-class-overview.md)

