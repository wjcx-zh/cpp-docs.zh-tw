---
title: "IOleInPlaceActiveObjectImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ContextSensitiveHelp
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::EnableModeless
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::GetWindow
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnDocWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::OnFrameWindowActivate
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::ResizeBorder
- ATLCTL/ATL::IOleInPlaceActiveObjectImpl::TranslateAccelerator
dev_langs:
- C++
helpviewer_keywords:
- IOleInPlaceActiveObjectImpl class
- ActiveX controls [C++], communication between container and control
- IOleInPlaceActiveObject, ATL implementation
ms.assetid: 44e6cc6d-a2dc-4187-98e3-73cf0320dea9
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
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 766ac40bb0a09902914feab1acc54a960261a768
ms.lasthandoff: 02/24/2017

---
# <a name="ioleinplaceactiveobjectimpl-class"></a>IOleInPlaceActiveObjectImpl 類別
這個類別提供方法協助就地控制項與其容器之間的通訊。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>
class IOleInPlaceActiveObjectImpl
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleInPlaceActiveObjectImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IOleInPlaceActiveObjectImpl::ContextSensitiveHelp](#contextsensitivehelp)|啟用即時線上說明。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleInPlaceActiveObjectImpl::EnableModeless](#enablemodeless)|可讓非強制回應對話方塊。 ATL 實作會傳回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::GetWindow](#getwindow)|取得視窗控制代碼。|  
|[IOleInPlaceActiveObjectImpl::OnDocWindowActivate](#ondocwindowactivate)|當容器的文件視窗是啟用或停用通知控制項。 ATL 實作會傳回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::OnFrameWindowActivate](#onframewindowactivate)|當容器的最上層框架視窗是啟用或停用通知控制項。 ATL 實作會傳回|  
|[IOleInPlaceActiveObjectImpl::ResizeBorder](#resizeborder)|通知控制項需要調整大小框線。 ATL 實作會傳回`S_OK`。|  
|[IOleInPlaceActiveObjectImpl::TranslateAccelerator](#translateaccelerator)|處理從容器的功能表快速鍵訊息。 ATL 實作會傳回**E_NOTIMPL**。|  
  
  
## <a name="remarks"></a>備註  
 [IOleInPlaceActiveObject](http://msdn.microsoft.com/library/windows/desktop/ms691299)介面協助進行就地控制項與其容器之間的通訊，比方說，通訊作用中狀態的控制項和容器，並通知控制項需要調整本身大小。 類別`IOleInPlaceActiveObjectImpl`提供的預設實作`IOleInPlaceActiveObject`，並支援**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleInPlaceActiveObject`  
  
 `IOleInPlaceActiveObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="contextsensitivehelp"></a>IOleInPlaceActiveObjectImpl::ContextSensitiveHelp  
 啟用即時線上說明。  
  
```
HRESULT ContextSensitiveHelp(BOOL fEnterMode);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleWindow::ContextSensitiveHelp](http://msdn.microsoft.com/library/windows/desktop/ms680059)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="enablemodeless"></a>IOleInPlaceActiveObjectImpl::EnableModeless  
 可讓非強制回應對話方塊。  
  
```
HRESULT EnableModeless(BOOL fEnable);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceActiveObject::EnableModeless](http://msdn.microsoft.com/library/windows/desktop/ms680115)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getwindow"></a>IOleInPlaceActiveObjectImpl::GetWindow  
 容器會呼叫此函式可取得控制項的視窗控制代碼。  
  
```
HRESULT GetWindow(HWND* phwnd);
```  
  
### <a name="remarks"></a>備註  
 某些容器無法運作，無視窗，即使它是目前的視窗型控制項。 在 ATL 的實作中，如果**CComControl::m_bWasOnceWindowless**資料成員是**TRUE**，此函數會傳回**E_FAIL**。 否則，如果\* *phwnd*不**NULL**，`GetWindow`指派*phwnd* control 類別資料成員`m_hWnd`，並傳回`S_OK`。  
  
 請參閱[IOleWindow::GetWindow](http://msdn.microsoft.com/library/windows/desktop/ms687282)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="ondocwindowactivate"></a>IOleInPlaceActiveObjectImpl::OnDocWindowActivate  
 當容器的文件視窗是啟用或停用通知控制項。  
  
```
HRESULT OnDocWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceActiveObject::OnDocWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms687281)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onframewindowactivate"></a>IOleInPlaceActiveObjectImpl::OnFrameWindowActivate  
 當容器的最上層框架視窗是啟用或停用通知控制項。  
  
```
HRESULT OnFrameWindowActivate(BOOL fActivate);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceActiveObject::OnFrameWindowActivate](http://msdn.microsoft.com/library/windows/desktop/ms683969)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="resizeborder"></a>IOleInPlaceActiveObjectImpl::ResizeBorder  
 通知控制項需要調整大小框線。  
  
```
HRESULT ResizeBorder(
    LPRECT prcBorder,
    IOleInPlaceUIWindow* pUIWindow,
    BOOL fFrameWindow);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceActiveObject::ResizeBorder](http://msdn.microsoft.com/library/windows/desktop/ms680053)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="translateaccelerator"></a>IOleInPlaceActiveObjectImpl::TranslateAccelerator  
 處理從容器的功能表快速鍵訊息。  
  
```
HRESULT TranslateAccelerator(LPMSG lpmsg);
```  
  
### <a name="return-value"></a>傳回值  
 這個方法支援下列傳回值：  
  
 `S_OK`如果訊息已成功地轉譯。  
  
 **S_FALSE**如果訊息未被翻譯。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleInPlaceActiveObject::TranslateAccelerator](http://msdn.microsoft.com/library/windows/desktop/ms693360)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)  
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)  
 [類別概觀](../../atl/atl-class-overview.md)

