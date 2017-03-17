---
title: "IOleObjectImpl 類別 |Microsoft 文件"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.openlocfilehash: b0b471b997bfdb4062f00b40864c347db78b114a
ms.lasthandoff: 02/24/2017

---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 類別
這個類別會實作**IUnknown**則是透過該容器與其通訊的控制項的主要介面。  
  
> [!IMPORTANT]
>  這個類別及其成員無法在 [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)]中執行的應用程式內使用。  
  
## <a name="syntax"></a>語法  
  
```
template<class T>  
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```  
  
#### <a name="parameters"></a>參數  
 `T`  
 您的類別，衍生自`IOleObjectImpl`。  
  
## <a name="members"></a>Members  
  
### <a name="public-methods"></a>公用方法  
  
|名稱|說明|  
|----------|-----------------|  
|[IOleObjectImpl::Advise](#advise)|建立控制諮詢連接。|  
|[IOleObjectImpl::Close](#close)|變更控制項狀態執行載入。|  
|[IOleObjectImpl::DoVerb](#doverb)|會告訴控制項執行其中一個列舉的動作。|  
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|會告訴控制項来捨棄它維護任何復原狀態。|  
|[IOleObjectImpl::DoVerbHide](#doverbhide)|會從檢視移除其使用者介面控制項的告知。|  
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|執行控制項並安裝它的視窗，但不會安裝控制項的使用者介面。|  
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|導致必須在個別視窗中的 開啟編輯控制項。|  
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|當使用者按兩下控制項時，會執行指定的動作。 控制項定義的動作，一般而言，若要啟動控制就地。|  
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向使用者顯示的最新插入的控制項。|  
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
|[IOleObjectImpl::InitFromData](#initfromdata)|初始化的控制項，從選取的資料。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::IsUpToDate](#isuptodate)|檢查控制項是否為最新狀態。 ATL 實作會傳回`S_OK`。|  
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)捨棄復原狀態之後。|  
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|由呼叫[DoVerbHide](#doverbhide)之後隱藏控制項。|  
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動之後。|  
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|由呼叫[DoVerbOpen](#doverbopen)控制項已開啟另一個視窗中進行編輯之後。|  
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項變成可見之後。|  
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)控制項的使用者介面啟動之後。|  
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)捨棄之前復原狀態。|  
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|由呼叫[DoVerbHide](#doverbhide)隱藏控制項之前。|  
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。|  
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|由呼叫[DoVerbOpen](#doverbopen)開啟在另一個視窗中編輯控制項之前。|  
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|由呼叫[DoVerbShow](#doverbshow)控制項變成可見之前。|  
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟動控制項的使用者介面。|  
|[IOleObjectImpl::SetClientSite](#setclientsite)|告訴用戶端中的站台容器控制項。|  
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|如果有的話，請至控制項的應用程式，建議色彩配置。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::SetExtent](#setextent)|設定控制項的顯示區域的範圍。|  
|[IOleObjectImpl::SetHostNames](#sethostnames)|會告訴控制項容器文件容器應用程式的名稱。|  
|[IOleObjectImpl::SetMoniker](#setmoniker)|會告訴它 moniker 的控制項。 ATL 實作會傳回**E_NOTIMPL**。|  
|[IOleObjectImpl::Unadvise](#unadvise)|刪除與控制諮詢連接。|  
|[IOleObjectImpl::Update](#update)|更新控制項。 ATL 實作會傳回`S_OK`。|  
  
## <a name="remarks"></a>備註  
 [IOleObject](http://msdn.microsoft.com/library/windows/desktop/dd542709)介面是透過該容器與其通訊的控制項的主要介面。 類別`IOleObjectImpl`提供此介面的預設實作，並且實作**IUnknown**傳送資訊給傾印裝置在偵錯組建。  
  
 **相關文章** [ATL 教學課程](../../atl/active-template-library-atl-tutorial.md)，[建立 ATL 專案](../../atl/reference/creating-an-atl-project.md)  
  
## <a name="inheritance-hierarchy"></a>繼承階層  
 `IOleObject`  
  
 `IOleObjectImpl`  
  
## <a name="requirements"></a>需求  
 **標頭︰** atlctl.h  
  
##  <a name="advise"></a>IOleObjectImpl::Advise  
 建立控制諮詢連接。  
  
```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Advise](http://msdn.microsoft.com/library/windows/desktop/ms686573)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="close"></a>IOleObjectImpl::Close  
 變更控制項狀態執行載入。  
  
```
STDMETHOD(Close)(DWORD dwSaveOption);
```  
  
### <a name="remarks"></a>備註  
 控制項就會停用，如果存在的話，會終結控制項視窗。 如果控制項類別資料成員[CComControlBase::m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)是**TRUE**和`dwSaveOption`參數是`OLECLOSE_SAVEIFDIRTY`或`OLECLOSE_PROMPTSAVE`，控制項的屬性會儲存在關閉之前。  
  
 保留在控制項類別資料成員的指標[CComControlBase::m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)發行時，資料成員和[CComControlBase::m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd)， [CComControlBase::m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless)，和[CComControlBase::m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)設為**FALSE**。  
  
 請參閱[IOleObject::Close](http://msdn.microsoft.com/library/windows/desktop/ms683922)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="doverb"></a>IOleObjectImpl::DoVerb  
 會告訴控制項執行其中一個列舉的動作。  
  
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
 值而定`iVerb`，其中一個 ATL `DoVerb` helper 函式呼叫，如下所示︰  
  
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
  
 請參閱[IOleObject::DoVerb](http://msdn.microsoft.com/library/windows/desktop/ms694508)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="doverbdiscardundo"></a>IOleObjectImpl::DoVerbDiscardUndo  
 會告訴控制項来捨棄它維護任何復原狀態。  
  
```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器會想要繪製的控制項。  
  
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
 [in]指標，該矩形容器會想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作。  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
##  <a name="doverbinplaceactivate"></a>IOleObjectImpl::DoVerbInPlaceActivate  
 執行控制項並安裝它的視窗，但不會安裝控制項的使用者介面。  
  
```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器會想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 藉由呼叫啟動就地控制項[CComControlBase::InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate)。 除非控制項類別資料成員`m_bWindowOnly`是**TRUE**，`DoVerbInPlaceActivate`第一次嘗試啟動該控制項做為無視窗控制項 (可能只有容器支援[IOleInPlaceSiteWindowless](http://msdn.microsoft.com/library/windows/desktop/ms682300))。 如果失敗，則函式會嘗試啟動該控制項擴充功能 (可能只有容器支援[IOleInPlaceSiteEx](http://msdn.microsoft.com/library/windows/desktop/ms693461))。 如果失敗，則函式會嘗試啟動該控制項沒有的擴充功能 (可能只有容器支援[IOleInPlaceSite](http://msdn.microsoft.com/library/windows/desktop/ms686586))。 如果啟動成功，函式會告知容器已啟動控制項。  
  
##  <a name="doverbopen"></a>IOleObjectImpl::DoVerbOpen  
 導致必須在個別視窗中的 開啟編輯控制項。  
  
```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器會想要繪製的控制項。  
  
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
 [in]指標，該矩形容器會想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
### <a name="remarks"></a>備註  
 根據預設，設定要顯示屬性頁。 您可以覆寫控制項類別中叫用不同的行為上按兩下。例如，播放視訊，或移就地啟用作用中。  
  
##  <a name="doverbshow"></a>IOleObjectImpl::DoVerbShow  
 會告知容器將控制項設為可見。  
  
```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器會想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="doverbuiactivate"></a>IOleObjectImpl::DoVerbUIActivate  
 啟動控制項的使用者介面，並告知容器，其功能表複合功能表所取代。  
  
```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```  
  
### <a name="parameters"></a>參數  
 `prcPosRec`  
 [in]指標，該矩形容器會想要繪製的控制項。  
  
 *hwndParent*  
 [in]包含控制項的視窗控制代碼。 不使用 ATL 實作。  
  
### <a name="return-value"></a>傳回值  
 其中一個標準`HRESULT`值。  
  
##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise  
 提供對這個控制項的已註冊諮詢連接的列舉型別。  
  
```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::EnumAdvise](http://msdn.microsoft.com/library/windows/desktop/ms682355)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs  
 對這個控制項提供已註冊的動作 （動詞命令） 的列舉型別，藉由呼叫**OleRegEnumVerbs**。  
  
```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```  
  
### <a name="remarks"></a>備註  
 您可以加入您的專案.rgs 檔動詞命令。 例如，請參閱 CIRCCTL。在 RGS [CIRC](../../visual-cpp-samples.md)範例。  
  
 請參閱[IOleObject::EnumVerbs](http://msdn.microsoft.com/library/windows/desktop/ms692781)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite  
 將指標放在控制項類別資料成員[CComControlBase::m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)到*ppClientSite*和指標的參考計數遞增。  
  
```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms692603)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 請參閱[IOleObject::GetClipboardData](http://msdn.microsoft.com/library/windows/desktop/ms682288)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getextent"></a>IOleObjectImpl::GetExtent  
 擷取以 himetric 為單位 （每個單位&0;.01 公釐） 的執行控制項的顯示大小。  
  
```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>備註  
 大小會儲存在控制項類別資料成員[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。  
  
 請參閱[IOleObject::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms692325)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getmiscstatus"></a>IOleObjectImpl::GetMiscStatus  
 將指標傳回至控制項的已註冊的狀態資訊，藉由呼叫**OleRegGetMiscStatus**。  
  
```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>備註  
 狀態資訊包括支援的控制項和呈現資料的行為。 您可以加入您的專案.rgs 檔案狀態資訊。  
  
 請參閱[IOleObject::GetMiscStatus](http://msdn.microsoft.com/library/windows/desktop/ms678521)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
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
 請參閱[IOleObject::GetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms686576)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID  
 傳回控制項的類別識別項。  
  
```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::GetUserClassID](http://msdn.microsoft.com/library/windows/desktop/ms682313)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="getusertype"></a>IOleObjectImpl::GetUserType  
 傳回控制項的使用者型別名稱，藉由呼叫**OleRegGetUserType**。  
  
```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```  
  
### <a name="remarks"></a>備註  
 用於使用者介面項目，例如功能表和對話方塊中顯示的使用者型別名稱。 您可以變更您的專案.rgs 檔案中的使用者類型名稱。  
  
 請參閱[IOleObject::GetUserType](http://msdn.microsoft.com/library/windows/desktop/ms688643)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData  
 初始化的控制項，從選取的資料。  
  
```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::InitFromData](http://msdn.microsoft.com/library/windows/desktop/ms688510)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate  
 檢查控制項是否為最新狀態。  
  
```
STDMETHOD(IsUpToDate)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::IsUpToDate](http://msdn.microsoft.com/library/windows/desktop/ms686624)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="onpostverbdiscardundo"></a>IOleObjectImpl::OnPostVerbDiscardUndo  
 由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)捨棄復原狀態之後。  
  
```
HRESULT OnPostVerbDiscardUndo();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼後捨棄復原狀態。  
  
##  <a name="onpostverbhide"></a>IOleObjectImpl::OnPostVerbHide  
 由呼叫[DoVerbHide](#doverbhide)之後隱藏控制項。  
  
```
HRESULT OnPostVerbHide();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼之後隱藏控制項。  
  
##  <a name="onpostverbinplaceactivate"></a>IOleObjectImpl::OnPostVerbInPlaceActivate  
 由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動之後。  
  
```
HRESULT OnPostVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法與您想要執行的程式碼之後就地啟動。  
  
##  <a name="onpostverbopen"></a>IOleObjectImpl::OnPostVerbOpen  
 由呼叫[DoVerbOpen](#doverbopen)控制項已開啟另一個視窗中進行編輯之後。  
  
```
HRESULT OnPostVerbOpen();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以您想要控制開啟另一個視窗中進行編輯之後執行的程式碼。  
  
##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow  
 由呼叫[DoVerbShow](#doverbshow)控制項變成可見之後。  
  
```
HRESULT OnPostVerbShow();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以您想要控制變成可見之後執行的程式碼。  
  
##  <a name="onpostverbuiactivate"></a>IOleObjectImpl::OnPostVerbUIActivate  
 由呼叫[DoVerbUIActivate](#doverbuiactivate)控制項的使用者介面啟動之後。  
  
```
HRESULT OnPostVerbUIActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 覆寫這個方法，以您想要啟用控制項的使用者介面之後執行的程式碼。  
  
##  <a name="onpreverbdiscardundo"></a>IOleObjectImpl::OnPreVerbDiscardUndo  
 由呼叫[DoVerbDiscardUndo](#doverbdiscardundo)捨棄之前復原狀態。  
  
```
HRESULT OnPreVerbDiscardUndo();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要避免捨棄復原狀態，會覆寫這個方法，傳回錯誤 HRESULT。  
  
##  <a name="onpreverbhide"></a>IOleObjectImpl::OnPreVerbHide  
 由呼叫[DoVerbHide](#doverbhide)隱藏控制項之前。  
  
```
HRESULT OnPreVerbHide();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項被隱藏，覆寫這個方法傳回錯誤 HRESULT。  
  
##  <a name="onpreverbinplaceactivate"></a>IOleObjectImpl::OnPreVerbInPlaceActivate  
 由呼叫[DoVerbInPlaceActivate](#doverbinplaceactivate)就地啟動控制項之前。  
  
```
HRESULT OnPreVerbInPlaceActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項被就地啟動，會覆寫這個方法，傳回錯誤 HRESULT。  
  
##  <a name="onpreverbopen"></a>IOleObjectImpl::OnPreVerbOpen  
 由呼叫[DoVerbOpen](#doverbopen)開啟在另一個視窗中編輯控制項之前。  
  
```
HRESULT OnPreVerbOpen();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項正在開啟另一個視窗中進行編輯，覆寫這個方法傳回錯誤 HRESULT。  
  
##  <a name="onpreverbshow"></a>IOleObjectImpl::OnPreVerbShow  
 由呼叫[DoVerbShow](#doverbshow)控制項變成可見之前。  
  
```
HRESULT OnPreVerbShow();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項被顯示出來，覆寫這個方法傳回錯誤 HRESULT。  
  
##  <a name="onpreverbuiactivate"></a>IOleObjectImpl::OnPreVerbUIActivate  
 由呼叫[DoVerbUIActivate](#doverbuiactivate)之前已啟動控制項的使用者介面。  
  
```
HRESULT OnPreVerbUIActivate();
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 若要防止控制項的使用者介面，使其無法啟動，會覆寫這個方法，傳回錯誤 HRESULT。  
  
##  <a name="setclientsite"></a>IOleObjectImpl::SetClientSite  
 告訴用戶端中的站台容器控制項。  
  
```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```  
  
### <a name="remarks"></a>備註  
 接著方法會傳回`S_OK`。  
  
 請參閱[IOleObject::SetClientSite](http://msdn.microsoft.com/library/windows/desktop/ms684013)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme  
 如果有的話，請至控制項的應用程式，建議色彩配置。  
  
```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetColorScheme](http://msdn.microsoft.com/library/windows/desktop/ms683971)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setextent"></a>IOleObjectImpl::SetExtent  
 設定控制項的顯示區域的範圍。  
  
```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```  
  
### <a name="remarks"></a>備註  
 否則，`SetExtent`所指向的值會儲存`psizel`控制項類別資料成員中[CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)。 這個值是以 himetric 為單位 （每個單位&0;.01 公釐）。  
  
 如果控制項類別資料成員[CComControlBase::m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)是**TRUE**，`SetExtent`所指向的值也會儲存`psizel`控制項類別資料成員中[CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)。  
  
 如果控制項類別資料成員[CComControlBase::m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)是**TRUE**，`SetExtent`呼叫`SendOnDataChange`和`SendOnViewChange`註冊控制項的大小已變更的通知持有者的所有通知接收的通知。  
  
 請參閱[IOleObject::SetExtent](http://msdn.microsoft.com/library/windows/desktop/ms694330)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames  
 會告訴控制項容器文件容器應用程式的名稱。  
  
```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetHostNames](http://msdn.microsoft.com/library/windows/desktop/ms680642)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker  
 會告訴它 moniker 的控制項。  
  
```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```  
  
### <a name="return-value"></a>傳回值  
 傳回**E_NOTIMPL**。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::SetMoniker](http://msdn.microsoft.com/library/windows/desktop/ms679671)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="unadvise"></a>IOleObjectImpl::Unadvise  
 刪除儲存在控制項類別的諮詢連接`m_spOleAdviseHolder`資料成員。  
  
```
STDMETHOD(Unadvise)(DWORD dwConnection);
```  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Unadvise](http://msdn.microsoft.com/library/windows/desktop/ms693749)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
##  <a name="update"></a>IOleObjectImpl::Update  
 更新控制項。  
  
```
STDMETHOD(Update)(void);
```  
  
### <a name="return-value"></a>傳回值  
 傳回 `S_OK`。  
  
### <a name="remarks"></a>備註  
 請參閱[IOleObject::Update](http://msdn.microsoft.com/library/windows/desktop/ms679699)中[!INCLUDE[winSDK](../../atl/includes/winsdk_md.md)]。  
  
## <a name="see-also"></a>另請參閱  
 [CComControl 類別](../../atl/reference/ccomcontrol-class.md)   
 [ActiveX 控制項介面](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [類別概觀](../../atl/atl-class-overview.md)

