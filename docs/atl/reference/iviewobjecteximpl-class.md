---
title: "IViewObjectExImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::IViewObjectExImpl<T>
- ATL.IViewObjectExImpl
- ATL::IViewObjectExImpl
- ATL.IViewObjectExImpl<T>
- IViewObjectExImpl
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
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
ms.openlocfilehash: 2b585a056324507cc631e64e6dbe9d0ed610361d
ms.lasthandoff: 02/24/2017

---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 類別
這個類別會實作**IUnknown** ，提供的預設實作[IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IViewObjectExImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|繪製至裝置內容控制的表示法。|  
|[IViewObjectExImpl::Freeze](#freeze)|凍結控制項的繪製的表示，因此它並不會變更直到`Unfreeze`。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果有的話，擷取現有的控制項上，通知接收的連接。|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|傳回邏輯繪製的控制項所使用的調色盤。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](#getextent)|擷取控制項的顯示大小以 himetric 為單位 （每個單位&0;.01 公釐） 的控制項類別資料成員從[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供從容器做為使用者調整物件大小的提示。|  
|[IViewObjectExImpl::GetRect](#getrect)|傳回描述要求的繪圖外觀的矩形。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|傳回物件和支援繪圖外觀的不透明度的相關資訊。|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|檢查是否指定的點是在指定的矩形，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|檢查控制項的顯示矩形是否與指定的位置矩形中的任何時間點，並傳回**HITRESULT**值`pHitResult`。|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|設定控制項和通知接收之間的連接，以便接收可以收到有關控制項的檢視中的變更。|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes 控制項的繪製表示法。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)介面可讓控制項直接顯示本身也可以建立和管理通知接收通知的容器中控制項顯示的變更。 **IViewObjectEx**介面提供支援擴充的控制項的功能，例如繪圖、 非矩形和透明控制項和點擊測試 （例如，如何關閉滑鼠點按必須視為在控制項上）。 類別`IViewObjectExImpl`提供這些介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="a-namedrawa--iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw  
 繪製至裝置內容控制的表示法。  
  
```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```  
  
### <a name="remarks"></a>備註  
 這個方法會呼叫**CComControl::OnDrawAdvanced**接著呼叫您的控制項類別`OnDraw`方法。 `OnDraw`方法會自動加入至您的控制項類別的 ATL 控制項精靈建立您的控制項時。 精靈的預設`OnDraw`標籤 「 ATL 3.0 」 以繪製一個矩形。  
  
 請參閱[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namefreezea--iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectExImpl::Freeze  
 凍結控制項的繪製的表示，因此它並不會變更直到`Unfreeze`。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetadvisea--iviewobjecteximplgetadvise"></a><a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 如果有的話，擷取現有的控制項上，通知接收的連接。  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>備註  
 控制項類別資料成員中儲存之通知接收[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。  
  
 請參閱[IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetcolorseta--iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 傳回邏輯繪製的控制項所使用的調色盤。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetextenta--iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectExImpl::GetExtent  
 擷取控制項的顯示大小以 himetric 為單位 （每個單位&0;.01 公釐） 的控制項類別資料成員從[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetnaturalextenta--iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent  
 提供從容器做為使用者調整物件大小的提示。  
  
```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```  
  
### <a name="remarks"></a>備註  
 如果`dwAspect`是`DVASPECT_CONTENT`和*-> dwExtentMode pExtentInfo*是**DVEXTENT_CONTENT**，設定 * `psizel` control 類別資料成員[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否則，會傳回錯誤`HRESULT`。  
  
 請參閱[IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetrecta--iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect  
 傳回描述要求的繪圖外觀的矩形。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namegetviewstatusa--iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 傳回物件和支援繪圖外觀的不透明度的相關資訊。  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>備註  
 根據預設，ATL 設定`pdwStatus`，表示控制項支援**VIEWSTATUS_OPAQUE** (可能的值位於[forced VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)列舉型別)。  
  
 請參閱[IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namequeryhitpointa--iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 檢查是否指定的點是在指定的矩形，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。  
  
```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>備註  
 值可以是**HITRESULT_HIT**或**HITRESULT_OUTSIDE**。  
  
 如果`dwAspect`等於[DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，方法會傳回`S_OK`。 否則，方法會傳回**E_FAIL**。  
  
 請參閱[IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namequeryhitrecta--iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 檢查控制項的顯示矩形是否與指定的位置矩形中的任何時間點，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。  
  
```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>備註  
 值可以是**HITRESULT_HIT**或**HITRESULT_OUTSIDE**。  
  
 如果`dwAspect`等於[DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318)，方法會傳回`S_OK`。 否則，方法會傳回**E_FAIL**。  
  
 請參閱[IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-namesetadvisea--iviewobjecteximplsetadvise"></a><a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 設定控制項和通知接收之間的連接，以便接收可以收到有關控制項的檢視中的變更。  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>備註  

 將指標[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)通知接收上的介面會儲存在控制項類別資料成員[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。  

  
 請參閱[IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameunfreezea--iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 Unfreezes 控制項的繪製表示法。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="a-nameclosehandlea--iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 實作這個方法，以關閉此物件相關聯的控制代碼。  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>參數  
 *hHandle*  
 若要關閉控制代碼。  
  
### <a name="return-value"></a>傳回值  
 成功或失敗的錯誤 HRESULT 會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 傳遞至這個方法的控制代碼未與此物件呼叫先前關聯[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼顯示的簡單實作`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities #&135;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="a-nameexecutea--iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Execute  
 實作這個方法與這個物件相關聯的控制代碼會變成已收到訊號時執行程式碼。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>參數  
 `dwParam`  
 User 參數。  
  
 `hObject`  
 變成已收到訊號的控制代碼。  
  
### <a name="return-value"></a>傳回值  
 成功或失敗的錯誤 HRESULT 會傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼和 DWORD/指標傳遞給這個方法已與此物件的呼叫之前相關[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼顯示的簡單實作`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities #&136;](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教學課程](../../atl/active-template-library-atl-tutorial.md)   
 [建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [類別概觀](../../atl/atl-class-overview.md)

