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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 06ce03a896c9948bff14b4f91ae48000d07c3edd
ms.contentlocale: zh-tw
ms.lasthandoff: 02/24/2017

---
# <a name="ioleinplaceobjectwindowlessimpl-class"></a>IOleInPlaceObjectWindowlessImpl 類別
這個類別會實作**IUnknown** ，並提供啟用無視窗控制項接收視窗訊息，並參與拖放作業的方法。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class IOleInPlaceObjectWindowlessImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleInPlaceObjectWindowlessImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetDropTarget](#getdroptarget)|提供`IDropTarget`就地使用中的無視窗物件支援拖放介面。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::GetWindow](#getwindow)|取得視窗控制代碼。|  
|[IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate](#inplacedeactivate)|停用就地現用控制項。|  
|[IOleInPlaceObjectWindowlessImpl::OnWindowMessage](#onwindowmessage)|分派容器是就地啟用作用中的無視窗控制項的訊息。|  
|[IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo](#reactivateandundo)|重新啟動之前已停用的控制項。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceObjectWindowlessImpl::SetObjectRects](#setobjectrects)|表示顯示在就地控制項的哪個部分。|  
|[IOleInPlaceObjectWindowlessImpl::UIDeactivate](#uideactivate)|停用，並移除支援就地啟用的使用者介面。|  
  
## <a name="remarks"></a>備註  
 [IOleInPlaceObject](http://msdn.microsoft.com/library/windows/desktop/ms692646)介面管理重新啟用和停用就地的控制，以及判斷多少控制項應該為可見的。 [IOleInPlaceObjectWindowless](http://msdn.microsoft.com/library/windows/desktop/ms687304)介面啟用無視窗控制項接收視窗訊息，並參與拖放作業。 類別`IOleInPlaceObjectWindowlessImpl`提供的預設實作`IOleInPlaceObject`和`IOleInPlaceObjectWindowless`並實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleInPlaceObjectWindowless`  
  
 `IOleInPlaceObjectWindowlessImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceObjectWindowlessImpl::ContextSensitiveHelp  
 傳回**E_NOTIMPL**。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getdroptarget"></a>IOleInPlaceObjectWindowlessImpl::GetDropTarget  
 傳回**E_NOTIMPL**。  
  
```
HRESULT GetDropTarget(IDropTarget** ppDropTarget);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObjectWindowless::GetDropTarget](http://msdn.microsoft.com/library/windows/desktop/ms678535)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getwindow"></a>IOleInPlaceObjectWindowlessImpl::GetWindow  
 容器會呼叫此函式可取得控制項的視窗控制代碼。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>備註  
 某些容器無法運作，無視窗，即使它是目前的視窗型控制項。 在 ATL 的實作中，如果控制項類別資料成員`m_bWasOnceWindowless`是**TRUE**，此函數會傳回**E_FAIL**。 否則，如果*phwnd*不**NULL**，`GetWindow`設定\* *phwnd* control 類別資料成員`m_hWnd`，並傳回`S_OK`。  
  
 請參閱[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="inplacedeactivate"></a>IOleInPlaceObjectWindowlessImpl::InPlaceDeactivate  
 若要停用就地現用控制項容器呼叫。  
  
```
HRESULT InPlaceDeactivate(HWND* phwnd);
```  
  
### <a name="remarks"></a>備註  
 這個方法會執行完整或部分的停用，根據控制項的狀態。 必要時，控制項的使用者介面已停用，並終結控制項的視窗中，如果有的話。 容器會收到通知，控制項不再使用中的位置。 **IOleInPlaceUIWindow**交涉功能表和框線空間容器所使用的介面釋放。  
  
 請參閱[IOleInPlaceObject::InPlaceDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms679700)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onwindowmessage"></a>IOleInPlaceObjectWindowlessImpl::OnWindowMessage  
 分派容器是就地啟用作用中的無視窗控制項的訊息。  
  
```
HRESULT OnWindowMessage(
    UINT msg,
    WPARAM WParam,
    LPARAM LParam,
    LRESULT plResultParam);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObjectWindowless::OnWindowMessage](http://msdn.microsoft.com/library/windows/desktop/ms693783)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="reactivateandundo"></a>IOleInPlaceObjectWindowlessImpl::ReactivateAndUndo  
 傳回**E_NOTIMPL**。  
  
```
HRESULT ReactivateAndUndo();
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceObject::ReactivateAndUndo](http://msdn.microsoft.com/library/windows/desktop/ms691372)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setobjectrects"></a>IOleInPlaceObjectWindowlessImpl::SetObjectRects  
 呼叫以通知其大小和 （或） 位置已變更的控制項容器。  
  
```
HRESULT SetObjectRects(LPCRECT prcPos, LPCRECT prcClip);
```  
  
### <a name="remarks"></a>備註  
 更新控制項的`m_rcPos`資料成員和控制項顯示。 顯示只控制項交集的裁剪區域的一部分。 如果先前已裁剪控制項的顯示，但已移除裁剪，您就可以呼叫此函式重繪控制項的完整檢視。  
  
 請參閱[IOleInPlaceObject::SetObjectRects](http://msdn.microsoft.com/library/windows/desktop/ms683767)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="uideactivate"></a>IOleInPlaceObjectWindowlessImpl::UIDeactivate  
 停用和移除控制項的使用者介面支援就地啟動。  
  
```
HRESULT UIDeactivate();
```  
  
### <a name="remarks"></a>備註  
 設定控制項類別資料成員`m_bUIActive`至**FALSE**。 ATL 實作，這個函數一律會傳回`S_OK`。  
  
 請參閱[IOleInPlaceObject::UIDeactivate](http://msdn.microsoft.com/library/windows/desktop/ms693348)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [類別概觀](../../atl/atl-class-overview.md)

