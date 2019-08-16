---
title: IOleObjectImpl 類別
ms.date: 11/04/2016
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
helpviewer_keywords:
- ActiveX controls [C++], communication between container and control
- IOleObject, ATL implementation
- IOleObjectImpl class
ms.assetid: 59750b2d-1633-4a51-a4c2-6455b6b90c45
ms.openlocfilehash: ded158b0ec862de5b0d0b23dd4b9edb50ad577ef
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495735"
---
# <a name="ioleobjectimpl-class"></a>IOleObjectImpl 類別

這個類別`IUnknown`會執行, 而是容器用來與控制項通訊的主要介面。

> [!IMPORTANT]
>  這個類別及其成員無法在 Windows 執行階段中執行的應用程式中使用。

## <a name="syntax"></a>語法

```
template<class T>
class ATL_NO_VTABLE IOleObjectImpl : public IOleObject
```

#### <a name="parameters"></a>參數

*T*<br/>
衍生自`IOleObjectImpl`的類別。

## <a name="members"></a>成員

### <a name="public-methods"></a>公用方法

|名稱|描述|
|----------|-----------------|
|[IOleObjectImpl::Advise](#advise)|建立與控制項的諮詢連接。|
|[IOleObjectImpl::Close](#close)|將控制項狀態從 [執行中] 變更為 [已載入]。|
|[IOleObjectImpl::DoVerb](#doverb)|告知控制項執行其列舉的其中一個動作。|
|[IOleObjectImpl::DoVerbDiscardUndo](#doverbdiscardundo)|告訴控制項捨棄它正在維護的任何復原狀態。|
|[IOleObjectImpl::DoVerbHide](#doverbhide)|告訴控制項從 view 中移除其使用者介面。|
|[IOleObjectImpl::DoVerbInPlaceActivate](#doverbinplaceactivate)|會執行控制項並安裝它的視窗, 但不會安裝控制項的使用者介面。|
|[IOleObjectImpl::DoVerbOpen](#doverbopen)|使控制項在另一個視窗中開啟編輯。|
|[IOleObjectImpl::DoVerbPrimary](#doverbprimary)|當使用者按兩下控制項時, 執行指定的動作。 控制項會定義動作, 通常是就地啟動控制項。|
|[IOleObjectImpl::DoVerbShow](#doverbshow)|向使用者顯示新插入的控制項。|
|[IOleObjectImpl::DoVerbUIActivate](#doverbuiactivate)|就地啟用控制項, 並顯示控制項的使用者介面, 例如功能表和工具列。|
|[IOleObjectImpl::EnumAdvise](#enumadvise)|列舉控制項的諮詢連接。|
|[IOleObjectImpl::EnumVerbs](#enumverbs)|列舉控制項的動作。|
|[IOleObjectImpl::GetClientSite](#getclientsite)|抓取控制項的用戶端網站。|
|[IOleObjectImpl::GetClipboardData](#getclipboarddata)|從剪貼簿抓取資料。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleObjectImpl::GetExtent](#getextent)|抓取控制項顯示區域的範圍。|
|[IOleObjectImpl::GetMiscStatus](#getmiscstatus)|抓取控制項的狀態。|
|[IOleObjectImpl::GetMoniker](#getmoniker)|抓取控制項的名字。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleObjectImpl::GetUserClassID](#getuserclassid)|抓取控制項的類別識別碼。|
|[IOleObjectImpl::GetUserType](#getusertype)|抓取控制項的使用者類型名稱。|
|[IOleObjectImpl::InitFromData](#initfromdata)|從選取的資料初始化控制項。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleObjectImpl::IsUpToDate](#isuptodate)|檢查控制項是否為最新狀態。 ATL 實作為傳回 S_OK。|
|[IOleObjectImpl::OnPostVerbDiscardUndo](#onpostverbdiscardundo)|在捨棄復原狀態之後, 由[DoVerbDiscardUndo](#doverbdiscardundo)呼叫。|
|[IOleObjectImpl::OnPostVerbHide](#onpostverbhide)|在隱藏控制項之後, 由[DoVerbHide](#doverbhide)呼叫。|
|[IOleObjectImpl::OnPostVerbInPlaceActivate](#onpostverbinplaceactivate)|在就地啟用控制項之後, 由[DoVerbInPlaceActivate](#doverbinplaceactivate)呼叫。|
|[IOleObjectImpl::OnPostVerbOpen](#onpostverbopen)|在控制項已在另一個視窗中開啟以供編輯之後, 由[DoVerbOpen](#doverbopen)呼叫。|
|[IOleObjectImpl::OnPostVerbShow](#onpostverbshow)|當控制項已成為可見之後, 由[DoVerbShow](#doverbshow)呼叫。|
|[IOleObjectImpl::OnPostVerbUIActivate](#onpostverbuiactivate)|在控制項的使用者介面啟用之後, 由[DoVerbUIActivate](#doverbuiactivate)呼叫。|
|[IOleObjectImpl::OnPreVerbDiscardUndo](#onpreverbdiscardundo)|在捨棄復原狀態之前, 由[DoVerbDiscardUndo](#doverbdiscardundo)呼叫。|
|[IOleObjectImpl::OnPreVerbHide](#onpreverbhide)|在隱藏控制項之前, 由[DoVerbHide](#doverbhide)呼叫。|
|[IOleObjectImpl::OnPreVerbInPlaceActivate](#onpreverbinplaceactivate)|在就地啟用控制項之前, 由[DoVerbInPlaceActivate](#doverbinplaceactivate)呼叫。|
|[IOleObjectImpl::OnPreVerbOpen](#onpreverbopen)|在控制項已于另一個視窗中開啟以供編輯之前, 由[DoVerbOpen](#doverbopen)呼叫。|
|[IOleObjectImpl::OnPreVerbShow](#onpreverbshow)|在控制項已成為可見之前, 由[DoVerbShow](#doverbshow)呼叫。|
|[IOleObjectImpl::OnPreVerbUIActivate](#onpreverbuiactivate)|在控制項的使用者介面啟動之前, 由[DoVerbUIActivate](#doverbuiactivate)呼叫。|
|[IOleObjectImpl::SetClientSite](#setclientsite)|告訴控制項其在容器中的用戶端網站。|
|[IOleObjectImpl::SetColorScheme](#setcolorscheme)|針對控制項的應用程式 (如果有的話) 建議色彩配置。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleObjectImpl::SetExtent](#setextent)|設定控制項顯示區域的範圍。|
|[IOleObjectImpl::SetHostNames](#sethostnames)|告訴控制項容器應用程式和容器檔案的名稱。|
|[IOleObjectImpl::SetMoniker](#setmoniker)|告訴控制項其標記為何。 ATL 執行會傳回 E_NOTIMPL。|
|[IOleObjectImpl::Unadvise](#unadvise)|使用控制項刪除諮詢連接。|
|[IOleObjectImpl::Update](#update)|更新控制項。 ATL 實作為傳回 S_OK。|

## <a name="remarks"></a>備註

[IOleObject](/windows/win32/api/oleidl/nn-oleidl-ioleobject)介面是容器用來與控制項通訊的主要介面。 類別`IOleObjectImpl`提供此介面的預設執行, 並藉`IUnknown`由將資訊傳送至偵錯工具組建中的傾印裝置來實現。

**相關文章**[Atl 教學](../../atl/active-template-library-atl-tutorial.md)課程,[建立 atl 專案](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>繼承階層

`IOleObject`

`IOleObjectImpl`

## <a name="requirements"></a>需求

**標頭:** atlctl。h

##  <a name="advise"></a>IOleObjectImpl:: Advise

建立與控制項的諮詢連接。

```
STDMETHOD(Advise)(
    IAdviseSink* pAdvSink,
    DWORD* pdwConnection);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: Advise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-advise) 。

##  <a name="close"></a>IOleObjectImpl:: Close

將控制項狀態從 [執行中] 變更為 [已載入]。

```
STDMETHOD(Close)(DWORD dwSaveOption);
```

### <a name="remarks"></a>備註

停用控制項, 並終結控制項視窗 (如果有的話)。 如果控制項類別資料成員[CComControlBase:: m_bRequiresSave](../../atl/reference/ccomcontrolbase-class.md#m_brequiressave)為 TRUE, 而*DWSAVEOPTION*參數為 OLECLOSE_SAVEIFDIRTY 或 OLECLOSE_PROMPTSAVE, 則會在關閉之前儲存控制項屬性。

在控制項類別資料成員[CComControlBase:: m_spInPlaceSite](../../atl/reference/ccomcontrolbase-class.md#m_spinplacesite)和[CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink)中保存的指標會被釋放, 而資料成員[CComControlBase:: m_bNegotiatedWnd](../../atl/reference/ccomcontrolbase-class.md#m_bnegotiatedwnd), [CComControlBase:: m_bWndless](../../atl/reference/ccomcontrolbase-class.md#m_bwndless), 而[CComControlBase:: m_bInPlaceSiteEx](../../atl/reference/ccomcontrolbase-class.md#m_binplacesiteex)設定為 FALSE。

請參閱 Windows SDK 中的[IOleObject:: Close](/windows/win32/api/oleidl/nf-oleidl-ioleobject-close) 。

##  <a name="doverb"></a>  IOleObjectImpl::DoVerb

告知控制項執行其列舉的其中一個動作。

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

根據的值`iVerb`, 會呼叫其中一個 ATL `DoVerb` helper 函式, 如下所示:

|*iVerb*Value|DoVerb helper 函式, 名為|
|-------------------|-----------------------------------|
|OLEIVERB_DISCARDUNDOSTATE|[DoVerbDiscardUndo](#doverbdiscardundo)|
|OLEIVERB_HIDE|[DoVerbHide](#doverbhide)|
|OLEIVERB_INPLACEACTIVATE|[DoVerbInPlaceActivate](#doverbinplaceactivate)|
|OLEIVERB_OPEN|[DoVerbOpen](#doverbopen)|
|OLEIVERB_PRIMARY|[DoVerbPrimary](#doverbprimary)|
|OLEIVERB_PROPERTIES|[CComControlBase::DoVerbProperties](../../atl/reference/ccomcontrolbase-class.md#doverbproperties)|
|OLEIVERB_SHOW|[DoVerbShow](#doverbshow)|
|OLEIVERB_UIACTIVATE|[DoVerbUIActivate](#doverbuiactivate)|

請參閱 Windows SDK 中的[IOleObject::D overb](/windows/win32/api/oleidl/nf-oleidl-ioleobject-doverb) 。

##  <a name="doverbdiscardundo"></a>  IOleObjectImpl::DoVerbDiscardUndo

告訴控制項捨棄它正在維護的任何復原狀態。

```
HRESULT DoVerbDiscardUndo(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbhide"></a>  IOleObjectImpl::DoVerbHide

停用並移除控制項的使用者介面, 並隱藏控制項。

```
HRESULT DoVerbHide(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。 不會用於 ATL 執行中。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbinplaceactivate"></a>  IOleObjectImpl::DoVerbInPlaceActivate

會執行控制項並安裝它的視窗, 但不會安裝控制項的使用者介面。

```
HRESULT DoVerbInPlaceActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。 不會用於 ATL 執行中。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

藉由呼叫[CComControlBase:: InPlaceActivate](../../atl/reference/ccomcontrolbase-class.md#inplaceactivate), 就地啟用控制項。 除非控制項類別的資料成員`m_bWindowOnly`為 TRUE, `DoVerbInPlaceActivate`否則會先嘗試將控制項啟動為無視窗控制項 (可能只有在容器支援[IOleInPlaceSiteWindowless](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesitewindowless)時才會這樣做)。 如果失敗, 函式會嘗試使用擴充功能啟動控制項 (可能只有在容器支援[IOleInPlaceSiteEx](/windows/win32/api/ocidl/nn-ocidl-ioleinplacesiteex)時才會這麼做)。 如果失敗, 函式會嘗試啟動沒有擴充功能的控制項 (可能只有在容器支援[IOleInPlaceSite](/windows/win32/api/oleidl/nn-oleidl-ioleinplacesite)時才會這麼做)。 如果啟用成功, 函式會通知容器已啟動該控制項。

##  <a name="doverbopen"></a>IOleObjectImpl::D oVerbOpen

使控制項在另一個視窗中開啟編輯。

```
HRESULT DoVerbOpen(LPCRECT /* prcPosRect */, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。

### <a name="return-value"></a>傳回值

傳回 S_OK。

##  <a name="doverbprimary"></a>IOleObjectImpl::D oVerbPrimary

定義使用者按兩下控制項時所採取的動作。

```
HRESULT DoVerbPrimary(LPCRECT prcPosRect, HWND hwndParent);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

### <a name="remarks"></a>備註

根據預設, 設定以顯示內容頁。 您可以在控制項類別中覆寫此值, 以在按兩下時叫用不同的行為。例如, 播放影片或就地進入使用中狀態。

##  <a name="doverbshow"></a>  IOleObjectImpl::DoVerbShow

告訴容器將控制項設為可見。

```
HRESULT DoVerbShow(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。 不會用於 ATL 執行中。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="doverbuiactivate"></a>  IOleObjectImpl::DoVerbUIActivate

啟動控制項的使用者介面, 並通知容器其功能表正由複合功能表所取代。

```
HRESULT DoVerbUIActivate(LPCRECT prcPosRect, HWND /* hwndParent */);
```

### <a name="parameters"></a>參數

*prcPosRec*<br/>
在容器想要用來繪製控制項之矩形的指標。

*hwndParent*<br/>
在包含控制項之視窗的控制碼。 不會用於 ATL 執行中。

### <a name="return-value"></a>傳回值

其中一個標準 HRESULT 值。

##  <a name="enumadvise"></a>IOleObjectImpl::EnumAdvise

提供此控制項的已註冊諮詢連接列舉。

```
STDMETHOD(EnumAdvise)(IEnumSTATDATA** ppenumAdvise);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: EnumAdvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumadvise) 。

##  <a name="enumverbs"></a>IOleObjectImpl::EnumVerbs

藉由呼叫`OleRegEnumVerbs`, 提供這個控制項的已註冊動作 (動詞) 列舉。

```
STDMETHOD(EnumVerbs)(IEnumOLEVERB** ppEnumOleVerb);
```

### <a name="remarks"></a>備註

您可以將動詞新增至專案的 .rgs 檔案。 例如, 請參閱 CIRCCTL。[CIRC](../../overview/visual-cpp-samples.md)範例中的 RGS。

請參閱 Windows SDK 中的[IOleObject:: EnumVerbs](/windows/win32/api/oleidl/nf-oleidl-ioleobject-enumverbs) 。

##  <a name="getclientsite"></a>IOleObjectImpl::GetClientSite

將控制項類別資料成員[CComControlBase:: m_spClientSite](../../atl/reference/ccomcontrolbase-class.md#m_spclientsite)中的指標放入*ppClientSite*中, 並遞增指標上的參考計數。

```
STDMETHOD(GetClientSite)(IOleClientSite** ppClientSite);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: GetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclientsite) 。

##  <a name="getclipboarddata"></a>  IOleObjectImpl::GetClipboardData

從剪貼簿抓取資料。

```
STDMETHOD(GetClipboardData)(
    DWORD /* dwReserved */,
    IDataObject** /* ppDataObject */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: GetClipboardData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getclipboarddata) 。

##  <a name="getextent"></a>IOleObjectImpl:: GetExtent

以 HIMETRIC 單位 (每單位0.01 毫米) 抓取執行中控制項的顯示大小。

```
STDMETHOD(GetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

大小會儲存在控制項類別資料成員[CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中。

請參閱 Windows SDK 中的[IOleObject:: GetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getextent) 。

##  <a name="getmiscstatus"></a>  IOleObjectImpl::GetMiscStatus

藉由呼叫`OleRegGetMiscStatus`, 傳回控制項之已註冊狀態資訊的指標。

```
STDMETHOD(GetMiscStatus)(
    DWORD dwAspect,
    DWORD* pdwStatus);
```

### <a name="remarks"></a>備註

狀態資訊包含控制項和呈現資料所支援的行為。 您可以將狀態資訊加入至專案的 .rgs 檔案。

請參閱 Windows SDK 中的[IOleObject:: GetMiscStatus](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmiscstatus) 。

##  <a name="getmoniker"></a>IOleObjectImpl:: GetMoniker

抓取控制項的名字。

```
STDMETHOD(GetMoniker)(
    DWORD /* dwAssign */,
    DWORD /* dwWhichMoniker */,
    IMoniker** /* ppmk */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: GetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getmoniker) 。

##  <a name="getuserclassid"></a>IOleObjectImpl::GetUserClassID

傳回控制項的類別識別碼。

```
STDMETHOD(GetUserClassID)(CLSID* pClsid);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: GetUserClassID](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getuserclassid) 。

##  <a name="getusertype"></a>IOleObjectImpl::GetUserType

藉由呼叫`OleRegGetUserType`, 傳回控制項的使用者類型名稱。

```
STDMETHOD(GetUserType)(
    DWORD dwFormOfType,
    LPOLESTR* pszUserType);
```

### <a name="remarks"></a>備註

使用者類型名稱是用來在使用者介面專案 (例如功能表和對話方塊) 中顯示。 您可以變更專案的 .rgs 檔案中的使用者類型名稱。

請參閱 Windows SDK 中的[IOleObject:: GetUserType](/windows/win32/api/oleidl/nf-oleidl-ioleobject-getusertype) 。

##  <a name="initfromdata"></a>IOleObjectImpl::InitFromData

從選取的資料初始化控制項。

```
STDMETHOD(InitFromData)(
    IDataObject* /* pDataObject */,
    BOOL /* fCreation */,
    DWORD /* dwReserved */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: InitFromData](/windows/win32/api/oleidl/nf-oleidl-ioleobject-initfromdata) 。

##  <a name="isuptodate"></a>IOleObjectImpl::IsUpToDate

檢查控制項是否為最新狀態。

```
STDMETHOD(IsUpToDate)(void);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: IsUpToDate](/windows/win32/api/oleidl/nf-oleidl-ioleobject-isuptodate) 。

##  <a name="onpostverbdiscardundo"></a>  IOleObjectImpl::OnPostVerbDiscardUndo

在捨棄復原狀態之後, 由[DoVerbDiscardUndo](#doverbdiscardundo)呼叫。

```
HRESULT OnPostVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

使用您想要在復原狀態捨棄後執行的程式碼來覆寫此方法。

##  <a name="onpostverbhide"></a>  IOleObjectImpl::OnPostVerbHide

在隱藏控制項之後, 由[DoVerbHide](#doverbhide)呼叫。

```
HRESULT OnPostVerbHide();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

使用您想要在隱藏控制項之後執行的程式碼來覆寫這個方法。

##  <a name="onpostverbinplaceactivate"></a>  IOleObjectImpl::OnPostVerbInPlaceActivate

在就地啟用控制項之後, 由[DoVerbInPlaceActivate](#doverbinplaceactivate)呼叫。

```
HRESULT OnPostVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

以您想要在就地啟動控制項之後執行的程式碼覆寫此方法。

##  <a name="onpostverbopen"></a>  IOleObjectImpl::OnPostVerbOpen

在控制項已在另一個視窗中開啟以供編輯之後, 由[DoVerbOpen](#doverbopen)呼叫。

```
HRESULT OnPostVerbOpen();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

使用您想要在控制項已在另一個視窗中開啟以供編輯之後執行的程式碼, 覆寫此方法。

##  <a name="onpostverbshow"></a>IOleObjectImpl::OnPostVerbShow

當控制項已成為可見之後, 由[DoVerbShow](#doverbshow)呼叫。

```
HRESULT OnPostVerbShow();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

以您想要在控制項已顯示後執行的程式碼覆寫這個方法。

##  <a name="onpostverbuiactivate"></a>  IOleObjectImpl::OnPostVerbUIActivate

在控制項的使用者介面啟用之後, 由[DoVerbUIActivate](#doverbuiactivate)呼叫。

```
HRESULT OnPostVerbUIActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

使用您想要在控制項的使用者介面啟動之後執行的程式碼來覆寫這個方法。

##  <a name="onpreverbdiscardundo"></a>  IOleObjectImpl::OnPreVerbDiscardUndo

在捨棄復原狀態之前, 由[DoVerbDiscardUndo](#doverbdiscardundo)呼叫。

```
HRESULT OnPreVerbDiscardUndo();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止捨棄復原狀態, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbhide"></a>  IOleObjectImpl::OnPreVerbHide

在隱藏控制項之前, 由[DoVerbHide](#doverbhide)呼叫。

```
HRESULT OnPreVerbHide();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止隱藏控制項, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbinplaceactivate"></a>  IOleObjectImpl::OnPreVerbInPlaceActivate

在就地啟用控制項之前, 由[DoVerbInPlaceActivate](#doverbinplaceactivate)呼叫。

```
HRESULT OnPreVerbInPlaceActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項就地啟動, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbopen"></a>  IOleObjectImpl::OnPreVerbOpen

在控制項已于另一個視窗中開啟以供編輯之前, 由[DoVerbOpen](#doverbopen)呼叫。

```
HRESULT OnPreVerbOpen();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項在另一個視窗中開啟以進行編輯, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbshow"></a>  IOleObjectImpl::OnPreVerbShow

在控制項已成為可見之前, 由[DoVerbShow](#doverbshow)呼叫。

```
HRESULT OnPreVerbShow();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止控制項變成可見, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="onpreverbuiactivate"></a>  IOleObjectImpl::OnPreVerbUIActivate

在控制項的使用者介面啟動之前, 由[DoVerbUIActivate](#doverbuiactivate)呼叫。

```
HRESULT OnPreVerbUIActivate();
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

若要防止啟用控制項的使用者介面, 請覆寫此方法以傳回錯誤 HRESULT。

##  <a name="setclientsite"></a>  IOleObjectImpl::SetClientSite

告訴控制項其在容器中的用戶端網站。

```
STDMETHOD(SetClientSite)(IOleClientSite* pClientSite);
```

### <a name="remarks"></a>備註

然後, 方法會傳回 S_OK。

請參閱 Windows SDK 中的[IOleObject:: SetClientSite](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setclientsite) 。

##  <a name="setcolorscheme"></a>IOleObjectImpl::SetColorScheme

針對控制項的應用程式 (如果有的話) 建議色彩配置。

```
STDMETHOD(SetColorScheme)(LOGPALETTE* /* pLogPal */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: SetColorScheme](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setcolorscheme) 。

##  <a name="setextent"></a>IOleObjectImpl:: SetExtent

設定控制項顯示區域的範圍。

```
STDMETHOD(SetExtent)(
    DWORD dwDrawAspect,
    SIZEL* psizel);
```

### <a name="remarks"></a>備註

否則, `SetExtent`會將所指向`psizel`的值儲存在控制項類別資料成員[CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent)中。 此值為 HIMETRIC 單位 (每單位0.01 毫米)。

如果控制項類別資料成員[CComControlBase:: m_bResizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_bresizenatural)為 TRUE, `SetExtent`也會將所指向的`psizel`值儲存在控制項類別資料成員[CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural)中。

如果控制項類別資料成員[CComControlBase:: m_bRecomposeOnResize](../../atl/reference/ccomcontrolbase-class.md#m_brecomposeonresize)為 TRUE, `SetExtent`則會呼叫`SendOnViewChange` `SendOnDataChange`和, 以通知已向通知持有者註冊控制項大小已變更的所有諮詢接收器。

請參閱 Windows SDK 中的[IOleObject:: SetExtent](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setextent) 。

##  <a name="sethostnames"></a>IOleObjectImpl::SetHostNames

告訴控制項容器應用程式和容器檔案的名稱。

```
STDMETHOD(SetHostNames)(LPCOLESTR /* szContainerApp */, LPCOLESTR /* szContainerObj */);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: SetHostNames](/windows/win32/api/oleidl/nf-oleidl-ioleobject-sethostnames) 。

##  <a name="setmoniker"></a>IOleObjectImpl::SetMoniker

告訴控制項其標記為何。

```
STDMETHOD(SetMoniker)(
    DWORD /* dwWhichMoniker */,
    IMoniker** /* pmk */);
```

### <a name="return-value"></a>傳回值

傳回 E_NOTIMPL。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: SetMoniker](/windows/win32/api/oleidl/nf-oleidl-ioleobject-setmoniker) 。

##  <a name="unadvise"></a>IOleObjectImpl:: Unadvise

刪除儲存在控制項類別`m_spOleAdviseHolder`之資料成員中的諮詢連接。

```
STDMETHOD(Unadvise)(DWORD dwConnection);
```

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: Unadvise](/windows/win32/api/oleidl/nf-oleidl-ioleobject-unadvise) 。

##  <a name="update"></a>IOleObjectImpl:: Update

更新控制項。

```
STDMETHOD(Update)(void);
```

### <a name="return-value"></a>傳回值

傳回 S_OK。

### <a name="remarks"></a>備註

請參閱 Windows SDK 中的[IOleObject:: Update](/windows/win32/api/oleidl/nf-oleidl-ioleobject-update) 。

## <a name="see-also"></a>另請參閱

[CComControl 類別](../../atl/reference/ccomcontrol-class.md)<br/>
[ActiveX 控制項介面](/windows/win32/com/activex-controls-interfaces)<br/>
[類別總覽](../../atl/atl-class-overview.md)
