---
title: "IViewObjectExImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 742198b0bf6c5c615baed033e8a0fab7e73b06ac
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl 類別
這個類別會實作**IUnknown**和提供的預設實作[IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IViewObjectExImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|繪製至裝置內容控制的表示法。|  
|[IViewObjectExImpl::Freeze](#freeze)|凍結控制項的繪製的表示法，讓它不會變更直到`Unfreeze`。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|如果有的話，擷取現有的通知接收連接在控制項上。|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|傳回邏輯控制項用於繪製的色板。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetExtent](#getextent)|擷取控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐） 的控制項類別資料成員從[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|提供使用隨著使用者調整它的物件的容器大小的提示。|  
|[IViewObjectExImpl::GetRect](#getrect)|傳回描述要求的繪圖外觀的矩形。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|傳回物件和支援的繪圖外觀的不透明度的相關資訊。|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|檢查是否指定的點為指定的矩形中，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|檢查是否在控制項的顯示矩形重疊在指定的位置矩形內，任何時間點，並傳回**HITRESULT**值`pHitResult`。|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|設定控制項和通知接收之間的連線，讓接收通知的控制項檢視中變更。|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Unfreezes 控制項的繪製的表示法。 ATL 實作會傳回**E_NOTIMPL**。|  
  
## <a name="remarks"></a>備註  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763)， [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318)，和[IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)介面可讓控制項來顯示本身直接，也可以建立和管理通知接收通知容器中控制項顯示的變更。 **IViewObjectEx**介面提供支援擴充的控制項的功能，例如閃爍的繪圖、 非矩形和透明控制項，以及叫用測試 （例如，如何關閉滑鼠點按必須視為上控制項）。 類別`IViewObjectExImpl`提供預設的實作這些介面並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IViewObjectEx`  
  
 `IViewObjectExImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="draw"></a>IViewObjectExImpl::Draw  
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
 這個方法會呼叫**CComControl::OnDrawAdvanced**接著呼叫您的控制項類別`OnDraw`方法。 `OnDraw`方法會自動加入至您的控制項類別的 ATL 控制項精靈建立您的控制項時。 精靈的預設`OnDraw`繪製的矩形的標籤"ATL 3.0"。  
  
 請參閱[iviewobject:: Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) Windows SDK 中。  
  
##  <a name="freeze"></a>IViewObjectExImpl::Freeze  
 凍結控制項的繪製的表示法，讓它不會變更直到`Unfreeze`。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728) Windows SDK 中。  
  
##  <a name="getadvise"></a>IViewObjectExImpl::GetAdvise  
 如果有的話，擷取現有的通知接收連接在控制項上。  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>備註  
 控制項類別資料成員中儲存之通知接收[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)。  
  
 請參閱[IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772) Windows SDK 中。  
  
##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet  
 傳回邏輯控制項用於繪製的色板。 ATL 實作會傳回**E_NOTIMPL**。  
  
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
 請參閱[IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553) Windows SDK 中。  
  
##  <a name="getextent"></a>IViewObjectExImpl::GetExtent  
 擷取控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐） 的控制項類別資料成員從[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) Windows SDK 中。  
  
##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent  
 提供使用隨著使用者調整它的物件的容器大小的提示。  
  
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
 如果`dwAspect`是`DVASPECT_CONTENT`和*pExtentInfo]-> [dwExtentMode*是**DVEXTENT_CONTENT**，設定 *`psizel`至控制項類別資料成員[CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。 否則，會傳回錯誤`HRESULT`。  
  
 請參閱[IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718) Windows SDK 中。  
  
##  <a name="getrect"></a>IViewObjectExImpl::GetRect  
 傳回描述要求的繪圖外觀的矩形。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246) Windows SDK 中。  
  
##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus  
 傳回物件和支援的繪圖外觀的不透明度的相關資訊。  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>備註  
 根據預設，ATL 設定`pdwStatus`表示此控制項支援**VIEWSTATUS_OPAQUE** (可能的值位於[forced VIEWSTATUS](http://msdn.microsoft.com/library/windows/desktop/ms687201)列舉型別)。  
  
 請參閱[IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371) Windows SDK 中。  
  
##  <a name="queryhitpoint"></a>IViewObjectExImpl::QueryHitPoint  
 檢查是否指定的點為指定的矩形中，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。  
  
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
  
 請參閱[IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209) Windows SDK 中。  
  
##  <a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect  
 檢查是否在控制項的顯示矩形重疊在指定的位置矩形內，任何時間點，並傳回[HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187)值`pHitResult`。  
  
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
  
 請參閱[IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797) Windows SDK 中。  
  
##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise  
 設定控制項和通知接收之間的連線，讓接收通知的控制項檢視中變更。  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>備註  

 將指標[IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513)通知接收上的介面會儲存在控制項類別資料成員[CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink)。  

  
 請參閱[IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950) Windows SDK 中。  
  
##  <a name="unfreeze"></a>IViewObjectExImpl::Unfreeze  
 Unfreezes 控制項的繪製的表示法。 ATL 實作會傳回**E_NOTIMPL**。  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641) Windows SDK 中。  
  
##  <a name="closehandle"></a>IWorkerThreadClient::CloseHandle  
 實作這個方法關閉此控制代碼，這個物件相關聯。  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>參數  
 *hHandle*  
 若要關閉控制代碼。  
  
### <a name="return-value"></a>傳回值  
 在成功或失敗的錯誤 HRESULT 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼示範的簡單實作`IWorkerThreadClient::CloseHandle`。  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>IWorkerThreadClient::Execute  
 實作這個方法與這個物件相關聯的控制代碼會變成收到信號時執行程式碼。  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>參數  
 `dwParam`  
 User 參數。  
  
 `hObject`  
 被通知控制代碼。  
  
### <a name="return-value"></a>傳回值  
 在成功或失敗的錯誤 HRESULT 傳回 S_OK。  
  
### <a name="remarks"></a>備註  
 控制代碼和 DWORD/指標傳遞給這個方法是先前物件相關聯的呼叫所[CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle)。  
  
### <a name="example"></a>範例  
 下列程式碼示範的簡單實作`IWorkerThreadClient::Execute`。  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [教學課程](../../atl/active-template-library-atl-tutorial.md)   
 [建立的 ATL 專案](../../atl/reference/creating-an-atl-project.md)   
 [類別概觀](../../atl/atl-class-overview.md)
