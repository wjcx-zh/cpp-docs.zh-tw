---
title: "IOleObjectImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl
- ATLCTL/ATL::IOleObjectImpl::Advise
- ATLCTL/ATL::IOleObjectImpl::Close
- ATLCTL/ATL::IOleObjectImpl::DoVerb
- ATLCTL/ATL::IOleObjectImpl::DoVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::DoVerbHide
- ATLCTL/ATL::IOleObjectImpl::DoVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::DoVerbOpen
- ATLCTL/ATL::IOleObjectImpl::DoVerbPrimary
- ATLCTL/ATL::IOleObjectImpl::DoVerbShow
- ATLCTL/ATL::IOleObjectImpl::DoVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::EnumAdvise
- ATLCTL/ATL::IOleObjectImpl::EnumVerbs
- ATLCTL/ATL::IOleObjectImpl::GetClientSite
- ATLCTL/ATL::IOleObjectImpl::GetClipboardData
- ATLCTL/ATL::IOleObjectImpl::GetExtent
- ATLCTL/ATL::IOleObjectImpl::GetMiscStatus
- ATLCTL/ATL::IOleObjectImpl::GetMoniker
- ATLCTL/ATL::IOleObjectImpl::GetUserClassID
- ATLCTL/ATL::IOleObjectImpl::GetUserType
- ATLCTL/ATL::IOleObjectImpl::InitFromData
- ATLCTL/ATL::IOleObjectImpl::IsUpToDate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPostVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbDiscardUndo
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbHide
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbInPlaceActivate
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbOpen
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbShow
- ATLCTL/ATL::IOleObjectImpl::OnPreVerbUIActivate
- ATLCTL/ATL::IOleObjectImpl::SetClientSite
- ATLCTL/ATL::IOleObjectImpl::SetColorScheme
- ATLCTL/ATL::IOleObjectImpl::SetExtent
- ATLCTL/ATL::IOleObjectImpl::SetHostNames
- ATLCTL/ATL::IOleObjectImpl::SetMoniker
- ATLCTL/ATL::IOleObjectImpl::Unadvise
- ATLCTL/ATL::IOleObjectImpl::Update
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: f710953a32ccb32c63742ab28e84818f3a330336
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/21/2017
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 類別
這個類別會實作**IUnknown**和是透過此容器會控制與通訊的主要介面。  
  
> [!IMPORTANT]
>  這個類別及其成員不能在 Windows 執行階段中執行的應用程式。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleObjectImpl`。  
  
## <a name="members"></a>成員  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|描述|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|建立與控制項諮詢連接。|  
|[IOleObjectImpl::Close](#close)|從執行以載入控制項狀態變更。|  
|[IOleObjectImpl::DoVerb](#doverb)|指示控制項執行其中一個列舉的動作。|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|告知要捨棄任何復原狀態，它會維護的控制項。|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|告知要從檢視移除其使用者介面的控制項。|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|執行控制項及安裝其視窗，但不會安裝控制項的使用者介面。|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|導致透過個別視窗中的 開啟編輯控制項。|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|當使用者按兩下控制項時，會執行指定的動作。 控制項定義的動作，通常是為了啟用控制項就地。|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向使用者顯示的新插入的控制項。|  
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|會控制就地啟動，並顯示控制項的使用者介面，例如功能表和工具列。|  
|[IOleObjectImpl::EnumAdvise](#enumadvise)|列舉控制諮詢連接。|  
|[IOleObjectImpl::EnumVerbs](#enumverbs)|列舉在控制項的動作。|  
|[IOleObjectImpl::GetClientSite](#getclientsite)|擷取控制項的用戶端站台。|  
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|從剪貼簿擷取資料。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::GetExtent](#getextent)|擷取控制項的顯示區域的範圍。|  
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|擷取控制項的狀態。|  
|[IOleObjectImpl::GetMoniker](#getmoniker)|擷取控制項的 moniker。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|擷取控制項的類別識別項。|  
|[IOleObjectImpl::GetUserType](#getusertype)|擷取控制項的使用者類型名稱。|  
|[IOleObjectImpl::InitFromData](#initfromdata)|初始化從選取的資料控制項。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|檢查控制項是否為最新狀態。 ATL 實作會傳回`S_OK`。|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)之後會捨棄復原狀態。|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|由呼叫[DoVerbHide](#doverbhide)隱藏此控制項之後。|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟用控制項之後。|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|由呼叫[DoVerbOpen](#doverbopen)控制項開啟另一個視窗中進行編輯後。|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項進行可見之後。|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)後已啟動控制項的使用者介面。|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)復原之前的狀態會被捨棄。|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|由呼叫[DoVerbHide](#doverbhide)隱藏此控制項之前。|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|由呼叫[DoVerbOpen](#doverbopen)控制項已開啟以供在個別視窗中編輯之前。|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項進行可見之前。|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟用控制項的使用者介面。|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|指示控制項其容器中的用戶端站台的相關。|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|如果有的話，請至控制項的應用程式，建議色彩配置。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::SetExtent](#setextent)|設定控制項的顯示區域的範圍。|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|指示控制項容器應用程式和容器文件的名稱。|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|指示控制項其 moniker 是什麼。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::Unadvise](#unadvise)|刪除與控制項諮詢連接。|  
|[IOleObjectImpl::Update](#update)|更新控制項。 ATL 實作會傳回`S_OK`。|  
  
## <a name="remarks"></a>備註  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709)介面是透過此容器會控制與通訊的主要介面。 類別`IOleObjectImpl`提供此介面的預設實作，並實作**IUnknown**資訊傳送給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭：** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 建立與控制項諮詢連接。  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573) Windows SDK 中。  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 從執行以載入控制項狀態變更。  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>備註  
 控制項就會停用，如果存在的話，會終結控制項視窗。 如果控制項類別資料成員[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)是**TRUE**和`dwSaveOption`參數為`OLECLOSE_SAVEIFDIRTY`或`OLECLOSE_PROMPTSAVE`，儲存控制項的屬性之後再關閉。  
  
 控制項類別資料成員的指標保留[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)發行時，資料成員和[CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)， [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)，和[CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)設為**FALSE**。  
  
 請參閱[IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922) Windows SDK 中。  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 指示控制項執行其中一個列舉的動作。  
  
```
STDMETHOD(DoVerb)(
    LONG iVerb,
    LPMSG /* pMsg */,
    IOleClientSite* pActiveSite,
    LONG /* lindex */,
    HWND hwndParent,
    LPCRECT lprcPosRect);
```  
  
### <a name="remarks"></a>備註  
 值而定`iVerb`，ATL 的其中一個`DoVerb`helper 函式呼叫，如下所示：  
  
|*iVerb*值|DoVerb helper 函式呼叫|  
|-------------------|-----------------------------------|  
|**OLEIVERB_DISCARDUNDOSTATE**|[DoVerbDiscardUndo](#doverbdiscardundo)|  
|`OLEIVERB_HIDE`|[DoVerbHide](#doverbhide)|  
|**OLEIVERB_INPLACEACTIVATE**|[DoVerbInPlaceActivate](#doverbinplaceactivate)|  
|`OLEIVERB_OPEN`|[DoVerbOpen](#doverbopen)|  
|`OLEIVERB_PRIMARY`|[DoVerbPrimary](#doverbprimary)|  
|**OLEIVERB_PROPERTIES**|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|  
|`OLEIVERB_SHOW`|[DoVerbShow](#doverbshow)|  
|`OLEIVERB_UIACTIVATE`|[DoVerbUIActivate](#doverbuiactivate)|  
  
 請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508) Windows SDK 中。  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 告知要捨棄任何復原狀態，它會維護的控制項。  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="doverbhide"></a>IOleObjectImpl::DoVerbHide  
 停用和移除控制項的使用者介面，並隱藏控制項。  
  
```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作中。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 執行控制項及安裝其視窗，但不會安裝控制項的使用者介面。  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作中。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 藉由呼叫啟動就地控制項[CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)。 除非控制項類別資料成員`m_bWindowOnly`是**TRUE**，`DoVerbInPlaceActivate`第一次嘗試啟動為將無視窗控制項的控制項 (支援容器時，才可能[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300)). 如果失敗，則函式會嘗試啟動該控制項擴充功能 (可能只有容器支援[IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461))。 如果失敗，則函式會嘗試啟動該控制項沒有的擴充功能 (可能只有容器支援[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586))。 如果啟動成功，函式會告知容器已啟動控制項。  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 導致透過個別視窗中的 開啟編輯控制項。  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="doverbprimary"></a>IOleObjectImpl::DoVerbPrimary  
 定義當使用者按兩下控制項時所採取的動作。  
  
```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 根據預設，設定要顯示屬性頁。 您可以叫用不同的行為上按兩下; 在控制項類別中覆寫此例如，播放視訊，或移就地啟用作用中。  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 告知容器將控制項設為可見。  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作中。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 啟動控制項的使用者介面，並告知容器，要透過複合功能表取代其功能表。  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作中。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 提供對這個控制項的已註冊諮詢連接的列舉。  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355) Windows SDK 中。  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 提供對這個控制項的已註冊的動作 （動詞命令） 的列舉，藉由呼叫**OleRegEnumVerbs**。  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>備註  
 您可以加入您的專案.rgs 檔動詞命令。 例如，請參閱 CIRCCTL。中的 RGS [CIRC](../../visual-cpp-samples.md)範例。  
  
 請參閱[IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781) Windows SDK 中。  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 將指標放在控制項類別的資料成員[CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)到*ppClientSite*和指標的參考計數遞增。  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603) Windows SDK 中。  
  
##  <a name="getclipboarddata"></a>IOleObjectImpl::GetClipboardData  
 從剪貼簿擷取資料。  
  
```
STDMETHOD(GetClipboardData)(    
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288) Windows SDK 中。  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 擷取執行控制項的顯示大小以 himetric 為單位 （每個單位 0.01 公釐）。  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>備註  
 大小會控制類別資料成員中儲存[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
 請參閱[IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325) Windows SDK 中。  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 讓指標回到已註冊的狀態資訊的控制項，藉由呼叫**OleRegGetMiscStatus**。  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>備註  
 狀態資訊包括支援控制項和呈現資料的行為。 您可以加入您的專案.rgs 檔案狀態資訊。  
  
 請參閱[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521) Windows SDK 中。  
  
##  <a name="getmoniker"></a>IOleObjectImpl::GetMoniker  
 擷取控制項的 moniker。  
  
```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576) Windows SDK 中。  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 傳回控制項的類別識別項。  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313) Windows SDK 中。  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 傳回控制項的使用者類型名稱，藉由呼叫**OleRegGetUserType**。  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>備註  
 使用者類型名稱使用使用者介面項目，例如功能表和對話方塊中顯示。 您可以變更您的專案.rgs 檔中的使用者類型名稱。  
  
 請參閱[IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643) Windows SDK 中。  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 初始化從選取的資料控制項。  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510) Windows SDK 中。  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 檢查控制項是否為最新狀態。  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624) Windows SDK 中。  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)之後會捨棄復原狀態。  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼之後會捨棄復原狀態。  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 由呼叫[DoVerbHide](#doverbhide)隱藏此控制項之後。  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼之後隱藏此控制項。  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟用控制項之後。  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼之後就地啟動控制項。  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 由呼叫[DoVerbOpen](#doverbopen)控制項開啟另一個視窗中進行編輯後。  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行另一個視窗中進行編輯，開啟控制項之後的程式碼。  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 由呼叫[DoVerbShow](#doverbshow)控制項進行可見之後。  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行之後控制項所顯示的程式碼。  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 由呼叫[DoVerbUIActivate](#doverbuiactivate)後已啟動控制項的使用者介面。  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行後已啟動控制項的使用者介面的程式碼。  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)復原之前的狀態會被捨棄。  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要避免捨棄復原狀態，會覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 由呼叫[DoVerbHide](#doverbhide)隱藏此控制項之前。  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止隱藏控制項，請覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止就地啟動控制項，請覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 由呼叫[DoVerbOpen](#doverbopen)控制項已開啟以供在個別視窗中編輯之前。  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項正在開啟以供編輯個別視窗中，會覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 由呼叫[DoVerbShow](#doverbshow)控制項進行可見之前。  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止進行可見控制項，覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟用控制項的使用者介面。  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項的使用者介面正在啟動，請覆寫此方法以傳回錯誤 HRESULT。  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 指示控制項其容器中的用戶端站台的相關。  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>備註  
 方法接著會傳回`S_OK`。  
  
 請參閱[IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013) Windows SDK 中。  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 如果有的話，請至控制項的應用程式，建議色彩配置。  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971) Windows SDK 中。  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 設定控制項的顯示區域的範圍。  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>備註  
 否則，`SetExtent`儲存所指向的值`psizel`控制項類別資料成員中[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。 這個值是以 himetric 為單位 （每個單位 0.01 公釐）。  
  
 如果控制項類別資料成員[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)是**TRUE**，`SetExtent`也會儲存所指向的值`psizel`中控制項的類別資料成員[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。  
  
 如果控制項類別資料成員[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)是**TRUE**，`SetExtent`呼叫`SendOnDataChange`和`SendOnViewChange`通知註冊的所有諮詢接收通知控制項大小已變更的持有者。  
  
 請參閱[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330) Windows SDK 中。  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 指示控制項容器應用程式和容器文件的名稱。  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642) Windows SDK 中。  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 指示控制項其 moniker 是什麼。  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671) Windows SDK 中。  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 刪除儲存在控制項類別諮詢連接`m_spOleAdviseHolder`資料成員。  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749) Windows SDK 中。  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 更新控制項。  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699) Windows SDK 中。  
  
## <a name="see-also"></a>請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [類別概觀](../../atl/atl-class-overview.md)
