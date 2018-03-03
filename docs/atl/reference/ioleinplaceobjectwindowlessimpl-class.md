---
title: "IOleInPlaceObjectWindowlessImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetDropTarget
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::OnWindowMessage
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::SetObjectRects
- ATLCTL/ATL::IOleInPlaceObjectWindowlessImpl::UIDeactivate
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceObjectWindowless, ATL implementation
- activation [C++], ATL
- IOleInPlaceObjectWindowlessImpl class
- ActiveX controls [C++], communication between container and control
- controls [ATL], windowless
- deactivating ATL
ms.assetid: a2e0feb4-bc59-4adf-aab2-105457bbdbb4
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3f455172723be4f46751b45d244e74dda5fcacae
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 類別
這個類別會實作**IUnknown** ，並提供可讓無視窗控制項接收視窗訊息，並參與拖放作業的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleInPlaceObjectWindowlessImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供`IDropTarget`就地使用中的無視窗物件的支援拖放介面。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|取得視窗控制代碼。|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用就地現用控制項。|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|會從容器是就地啟用作用中的無視窗控制項的訊息分派。|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新啟動之前已停用的控制項。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|表示顯示就地控制項的哪個部分。|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用，並移除支援就地啟用的使用者介面。|  
  
## <a name="remarks"></a>備註  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)介面會管理重新啟用和停用就地的控制，並決定控制項中有多少應該為可見的。 [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304)介面可讓無視窗控制項接收視窗訊息，並參與拖放作業。 類別`IOleInPlaceObjectWindowlessImpl`提供的預設實作`IOleInPlaceObject`和`IOleInPlaceObjectWindowless`並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 傳回**E_NOTIMPL**。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059) Windows SDK 中。  
  
##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 傳回**E_NOTIMPL**。  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535) Windows SDK 中。  
  
##  <a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow  
 容器會呼叫此函式可取得控制項的視窗控制代碼。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>備註  
 某些容器與已無視窗，即使它是目前的視窗型控制項無法運作。 在 ATL 的實作中，如果控制項類別資料成員`m_bWasOnceWindowless`是**TRUE**，此函數會傳回**E_FAIL**。 否則，如果*phwnd*不**NULL**，`GetWindow`設定\* *phwnd*至控制項類別資料成員`m_hWnd`並傳回`S_OK`.  
  
 請參閱[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282) Windows SDK 中。  
  
##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 若要停用就地現用控制項容器所呼叫。  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>備註  
 這個方法會執行完整或部分的停用，視控制項的狀態而定。 如有必要，停用控制項的使用者介面，並終結控制項的視窗中，如果有的話。 容器被通知控制項不再作用中就地。 **IOleInPlaceUIWindow**協調功能表和框線空間容器所使用的介面釋放。  
  
 請參閱[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700) Windows SDK 中。  
  
##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 會從容器是就地啟用作用中的無視窗控制項的訊息分派。  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783) Windows SDK 中。  
  
##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 傳回**E_NOTIMPL**。  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372) Windows SDK 中。  
  
##  <a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 呼叫以通知已變更其大小和 （或） 位置的控制項的容器。  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>備註  
 更新控制項的`m_rcPos`資料成員和控制項顯示。 顯示只交集的裁剪區域控制項的一部分。 如果先前已裁剪控制項的顯示，但已移除裁剪，您就可以呼叫此函式重繪控制項的完整檢視。  
  
 請參閱[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767) Windows SDK 中。  
  
##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 停用和移除控制項的使用者介面，支援就地啟用。  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>備註  
 設定控制項類別資料成員`m_bUIActive`至**FALSE**。 ATL 實作，此函數永遠會傳回`S_OK`。  
  
 請參閱[IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)
